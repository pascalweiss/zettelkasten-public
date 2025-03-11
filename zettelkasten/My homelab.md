#draft #public

I see my homelab as a place where I can easily deploy software. This might either be for educational purposes, like testing out certain programming languages, frameworks or libraries, or it might be for prototyping of business ideas. 
The
### Infrastructure

#### Kubernetes cluster
My homeland is based on a kubernetes cluster, that runs on two workers ([[Lenovo V145-15AST]], [[Acer Extensa 5635Z]]) and a master ([[Minis Forum Venus Series UM773]]).

#### Version Control and CI
The git repository is provided by a self hosted gitlab instance. New commits must go through a MR review. With every MR, there is a CI pipeline which executes builds, tests, and a review-deployment. For more see [[homelab - gitlab]]

#### GitOps
The application deployment is automated with Flux (see [[FluxCD]]). Therefore it observes the git repository. If a change is detected, it automatically updates the corresponding resource. 
For more see [[public/zettelkasten/homelab - FluxCD]]


- [[homelab - DNS and VPN setup]]
- [[homelab - gitlab]]


### Various TODO
- [[homelab - Ingress]]

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

