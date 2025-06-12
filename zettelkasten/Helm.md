---
created: 2025-03-03T08:00
updated: 2025-06-12T23:45
---
#public
Kind of a package manager. Used for deploying and managing applications in a kubernetes cluster.

### How does it work
It is installed on a local machine or a deployment pipeline. It reads in helm charts and applies the contained manifests via the k8s API.

### Main elements of helm
- **Chart:** A package that defines a kubernetes application. It comprises multiple kubernetes manifests for installing the application
- **Values:** Provide the ability to define configuration parameters to a helm chart. This allows to configure the application without changing the helm chart itsel
- **Release:** An instance of a helm chart. I.e. a running application
- **Repositories:** Locations where helm charts are stored and published 


### Important commands
- **helm repo add**
- **helm search repo** 
- **helm install**
- **helm list**
- **helm Upgrade**
- **helm uninstall**

### Related links
- https://helm.sh
- https://artifacthub.io: An index for many helm charts, similar to dockerhub

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

