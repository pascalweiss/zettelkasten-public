---
created: 2025-03-03T08:00
updated: 2025-06-14T21:20
---
#public
This tutorial describes how to connect flux with an public oci based helm repository. For more information on oci, see [[OCI repositories - Open Container Initiative (specification)]]

### Goal
The goal is to install postgresql helm release, here https://bitnami.com/stack/postgresql/helm. It is provided via the Docker OCI repo.

### Tutorial
Create a new repo reference in `my-cluster`. Make sure, that the type is set to `oci`  

```yaml
apiVersion: source.toolkit.fluxcd.io/v1beta2  
kind: HelmRepository  
metadata:  
  name: bitnami # name of the HelmRepository resource  
  namespace: default  
spec:  
  type: oci  
  interval: 1m0s  
  url: oci://registry-1.docker.io/bitnamicharts
```
Then define the helm release. In this case, the secrets are provided in clear text. In a follow up tutorial, this is done using kubernetes secrets

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2beta1  
kind: HelmRelease  
metadata:  
  name: postgresql  
  namespace: default  
spec:  
  interval: 1m  
  chart:  
    spec:  
      chart: postgresql  
      version: '16.2.5'  
      sourceRef:  
        kind: HelmRepository  
        name: bitnami  
        namespace: default  
      interval: 1m
```
If you push it and reconcile the kustomization, it will be deployed.





### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

