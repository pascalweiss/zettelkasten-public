#public
This page describes how Flux CD interacts with Helm (see [[Helm]]). It shows how to create a helm chart and store it into a git repository. Then it describes how to configure flux, to observe this helm chart and deploy it to the kubernetes cluster.

In the **root** of the repository (_not_ under clusters) run the following commands:

```shelll
mkdir charts
cd charts
helm create nginx
```

Modify the nginx/values.yaml file as follows:

```yaml
ingress:  
  enabled: true # changed  
  className: "nginx" # changed  
  annotations: {}  
  # kubernetes.io/ingress.class: nginx    
  # kubernetes.io/tls-acme: "true"  
  hosts:  
    - host: "" # changed  
      paths:  
        - path: /  
          pathType: ImplementationSpecific
```

Create a Helm Release resource file in `clusters/my-clusters` path. The filename could be `nginx-helm-release.yaml`. The contents are as follows:

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2  
kind: HelmRelease  
metadata:  
  name: nginx  
  namespace: default  
spec:  
  interval: 1m # how often flux cd should check for updates in the helm release file  
  chart:  
    spec:  
      chart: ./charts/nginx  
      sourceRef:  
        kind: GitRepository  
        name: flux-system # this repo was defined for flux cd at bootstrapping  
        namespace: flux-system  
      interval: 1m # how often flux cd should check for updates in the helm chart file
```
Commit the changes to Git by running the following commands:

```shell
git checkout -b nginx-helm
git add -A
git commit -m "Adding the Nginx Helm chart and creating the Flux CD Helm Release resource"
git push --set-upstream origin nginx-helm
```

- Copy the MR link, open the browser, paste the link, merge the MR and return back to the terminal.
- Force Flux CD to do a reconciliation by running the following command:

```
flux reconcile kustomization flux-system --with-source
```

Observe the Helm Release resource and the pods:

```
kubectl get helmrelease
kubectl get pods
```

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

