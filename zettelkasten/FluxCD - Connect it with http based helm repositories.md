---
created: 2025-03-03T08:00
updated: 2025-06-14T21:20
---
#public
Flux can use helm repositories for retrieving helm charts and deploy them in the cluster. It automatically detects changes in the chart and makes sure, that the version in the cluster is the same.

### Tutorial
This tutorial is based on the setup, described here: [[ChartMuseum]].


#### Reference the helm repo
Given that Chartmuseum is running, it has to be added to the flux, by creating a file in `clusters/my-cluster` with the following content

```yaml
---  
apiVersion: source.toolkit.fluxcd.io/v1beta2  
kind: HelmRepository  
metadata:  
  name: myhelmrepo  
  namespace: default  
spec:  
  interval: 1m0s  
  url: http://<host>:8080  
  secretRef:  
    name: myhelmrepo-secret  
---  
apiVersion: v1  
kind: Secret  
metadata:  
  name: myhelmrepo-secret  
  namespace: default  
stringData:  
  username: "<username>"  
  password: "<password>"
```

Note: 
- the Url has to be the public IP, where chartmuseum is running (do not provide `localhost`)
- username and password are provided in clear text. This will be changed later on. 

#### Create a helm-release
Then a helm-release has to be defined. Therefore, create a file in the same directory with the following content:

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2beta1  
kind: HelmRelease  
metadata:  
  name: busybox  
  namespace: default  
spec:  
  interval: 1m  
  chart:  
    spec:  
      chart: busybox  
      version: 0.1.0  
      sourceRef:  
        kind: HelmRepository  
        name: myhelmrepo  
        namespace: default  
      interval: 1m
```
#### Apply the changes
The changes can be applied right away with: 
```shell
flux reconcile kustomization flux-system --with-source
```
Then the result can be inspected with:
```shell
kubectl get helmrelease
# and/or
kubectl get helmchart
# and/or
kubectl get pods
```


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

