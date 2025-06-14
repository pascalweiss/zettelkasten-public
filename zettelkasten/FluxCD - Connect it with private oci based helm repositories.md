---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
This tutorial describes how to connect flux to a private oci helm repository, that can only be accessed with credentials. We will
- create a helm chart for an apache server
- upload the package it to a private gitlab helm repository
- create a k8s secret for the credentials
- connect flux to the reposiotry using the secret
- create a helm release for the apache server

# Tutorial

### Create a helm package
First, create a helm chart for apache
```shell
helm create apache
```
- Open the `Chart.yaml`file and change `appVersion` to `2.4.57`
- Open the `values.yaml` file and change the image repository the be `httpd`instead of `nginx`
- Create a Helm package by running
```shell
helm package .
```

### Upload the package
Go to gitlab and create a private access token (PAT). Then login and use the PAT as password
```shell
helm registry login -u <username> registry.gitlab.com
```
Now push the previously created apache package
```shell
helm push apache-0.1.0.tgz oci://registry.gitlab.com/<username>/<repo>
```
### Create a secret
We will now create a secret, the access the uploaded helm package from the cluster. Therefore, create a base64 encoded string with the previously used PAT.
```shell
echo -n "<username>:<token>" | base64
```
The result is then used inside a json, which we then encode with base64 again.
```shell
echo "{  
  \"auths\": {  
    \"registry.gitlab.com\": {  
      \"auth\": \"<base64-encoded-username:password>\"  
    }  
  }  
}" | base64 -w 0
```
#### Alternative
After you logged into gitlab with helm, it is also possible get the json with
```shell
cat ~/.config/helm/registry/config.json
```
At least this should work on Linux. 

### Create a secret
You can either create the secret imperatively or declaratively. The **imperative** way secure, since it prevents that secrets are published in git. 

```shell
kubectl create secret docker-registry gitlab-credentials \
  --docker-username=<username> \
  --docker-password=<PAT> \
  --docker-server=registry.gitlab.com \
  --namespace=default
```

The **declarative** is better to maintain. It is described in the following, but note, that in the real world, you wouldn't store the PAT openly, as I do it here:

in `clusters/my-cluster`create a file secret-gitlab-oci.yaml:
```yaml
apiVersion: v1  
kind: Secret  
metadata:  
  name: gitlab-credentials  
  namespace: default  
data:  
  .dockerconfigjson: # base64 encoded PAT-json from "Create a secret" 
type: kubernetes.io/dockerconfigjson
```

### Create a helm repo
create a new yaml for the gitlab repo and reference the previously created secret by its name
```shell
apiVersion: source.toolkit.fluxcd.io/v1beta2  
kind: HelmRepository  
metadata:  
  name: gitlab  
  namespace: default  
spec:  
  type: oci  
  interval: 5m0s  
  url: oci://registry.gitlab.com/deciso78/homelab  
  secretRef:  
    name: gitlab-credentials
```

### Helm release
Finally we create a helm release from the helm repo
```shell
apiVersion: helm.toolkit.fluxcd.io/v2beta1  
kind: HelmRelease  
metadata:  
  name: apache  
  namespace: default  
spec:  
  interval: 5m  
  chart:  
    spec:  
      chart: apache  
      version: '0.1.0'  
      sourceRef:  
        kind: HelmRepository  
        name: gitlab  
        namespace: default
```

### Finished
Now push everything and do
```shell
flux reconcile kustomization flux-system --with-source
```
Verify the result with

```
kubectl get helmrepository
kubectl get helmrelease
kubectl get pods
```





### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

