#public

### Kubernetes cluster
My homeland is based on a kubernetes cluster, that runs on two workers ([[Lenovo V145-15AST]], [[Acer Extensa 5635Z]]) and a master ([[Minis Forum Venus Series UM773]]).

### GitOps
The application deployment is automated with Flux (see [[FluxCD]]). Therefore it observes the git repository. If a change is detected, it automatically updates the corresponding resource. 
For more see [[public/zettelkasten/homelab - FluxCD]]

### Version Control and CI
The git repository is provided by a self hosted gitlab instance. New commits must go through a MR review. With every MR, there is a CI pipeline which executes builds, tests, and a review-deployment. For more see [[homelab - gitlab]]


### Outgoing emails
For sending emails from inside of the cluster to the outside, there is a postfix (see [[Postfix - mail transfer agent]]) deployment. It sends emails to any recipient via mailgun (see [[tool - mailgun]]). 

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

