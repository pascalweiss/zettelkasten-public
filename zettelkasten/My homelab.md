---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public 

I see my homelab as a place where I can easily deploy software. This might either be for educational purposes, like testing out certain programming languages, frameworks or libraries, or it might be for prototyping of business ideas. 

### Requirements
I want to run multiple applications with certain tech stack. See requirements here:
[[homelab - requirements]]

### Infrastructure

#### Hardware
List of all hardware components, that are used in my homelab: [[homelab - hardware]]

#### Kubernetes cluster
My homeland is based on a kubernetes cluster, that runs on two workers ([[Lenovo V145-15AST]], [[Acer Extensa 5635Z]]) and two masters/workers (both ([[Minis Forum Venus Series UM773]])). I use microk8s from cannonical

#### Version Control and CI
The git repository is provided by a self hosted gitlab instance on one of the [[Minis Forum Venus Series UM773]]. Merges to the main branches must go through a MR review. With every MR, there is a CI pipeline which executes builds, tests, and a preview-deployment. For more see [[homelab - gitlab]]

#### GitOps for main branches
For each application, the main branches are deployed to the cluster with Flux (see [[FluxCD]]). For more see [[homelab - FluxCD]]

#### DNS and VPN
The domains `homelab.lan` or `*.homelab.lan` are resolved to 192.168.8.201 (this is the node where my ingress runs). The domain server is hosted on my router [[GL.iNet GL-MT6000]]. 
Also I have set up a OpenVPN server together with DynDNS, so that I can access my homelab from everywhere. 
For more, see [[homelab - DNS and VPN setup]]

#### Ingress
Every traffic that goes into my k8s cluster is routed through an ingress service. It has a set of rules with which requests are routed to the right apps, i.e. services. For more, see [[homelab - Ingress]].


### Projects
This section provides all projects, that are hosted in the cluster
- [[My digital garden]]


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

