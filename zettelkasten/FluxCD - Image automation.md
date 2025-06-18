---
created: 2024-11-22T17:12
updated: 2025-06-17T18:44
---
When docker containers are used in a kubernetes cluster, it is often required to update the container version, whenever a new image is published.

This is an alternative to the manual approach, where you upgrade the helm release version with a new helm chart version, which references a new image version. 

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

