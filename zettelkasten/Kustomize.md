#public 
A kubernetes tool for managing kubernetes configurations. It allows to "kustomize" Kubernetes manifests, without manipulating the corresponding original files. This is done by so called **Overlays**, in which the manipulation of the original resource is defined. Usually, these overlays are used to for adjusting kubernetes resources for specific environments (like dev, prod, testing).

### Example
In the following example, the `base/deployment.yaml` is adjusted with overlays to create a dev and a prod deployment.
```yml
.
├── base
│   └── kustomization.yaml
│   └── deployment.yaml
└── overlays
    ├── dev
    │   └── kustomization.yaml
    │   └── deployment-patch.yaml
    └── prod
        └── kustomization.yaml
        └── deployment-patch.yaml
```



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

