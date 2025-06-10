#public
A tool that helps to implement [[GitOps]] principles for kubernetes. It watches the git repository and automatically applies changes to the cluster. 

### Features
- **Automated deployment**: Changes that are made to the git repository are detected by flux. The state in the cluster is then synchronised, so that it matches the state in the repo
- **Multi Tenancy**: Allows to deploy to multiple clusters or namespaces. E.g. to Dev, Staging and Prod.
- **Integration with Git Providers**: Supports Github, Gitlab, Bitbucket

### Architecture
- **Flux Operator**: Runs inside the cluster. Observes changes in the git repository and applies changes to the cluster accordingly
- **Helm Operator**: Similar to the Flux Operator. Applies changes to helm releases, that are made to helm charts
- **Kustomization Operator**: Does the same as the Helm Operator, but with regards to kustomize

### Further Topics
- [[FluxCD - Image automation]]
- [[FluxCD - Commands and tips]]
- [[FluxCD - Preview deployments]]

#### Flux Basics
- [[FluxCD - Bootstrapping with Github]]
- [[FluxCD - Recreation to multiple clusters]]
- [[FluxCD - Handling git Access Tokens]]

#### Flux CD and Helm
- [[FluxCD - With git as helm charts source]]
- [[FluxCD - Modifying the Helm Chart and overriding the default values]]
- [[FluxCD - Connect it with a helm repository]]

### Related Links
- API Doc for yaml-files https://fluxcd.io/flux/components/source/api/
- Flux documentation: [[docu - flux]]


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

