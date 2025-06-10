#public
### Reconcile
Reconcile syncs the cluster state with the repo state. 

**Kustomization:** Reconciles a certain kustomization. E.g. `flux-system`.
`flux reconcile kustomization <kustomization-name> --with-source`

**Helm Releases:** reconciles a specific helm release.
`flux reconcile helmrelease <helm-release-name> -n <namespace>`

Note: if you try to redeploy a helm release, after the deployment was removed:
- Remove the `helm` release as well
- reconcile the `helmrelease`



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

