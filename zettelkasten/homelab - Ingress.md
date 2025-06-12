#public

a nginx that routes http requests to the right service. 
The routes are distinguished by 
- subdomain
- path

### Externally accessible
The ingress service is defined as Load Balancer. Thereby it is accessible from outside the cluster with an external IP (192.168.8.201). The external IP is resolved from `*.homelab.lan/*` by the DNS (see [[homelab - DNS and VPN setup]]).  

### Static IP
To ensure, that the the IP stays the same, the service must have a static assignment to a certain node. This is achieved with *nodeSelector*
```yaml
nodeSelector: 
  ingress-ready: "true" 
  kubernetes.io/os: linux
```
To couple it to a the right 192.168.8.201, it is required to label the corresponding node:
```bash
kubectl label node forum0 ingress-ready=true
```
  
### Single entry point
As an ingress service, it is able to route the incoming traffic to the right services. This way it is not required to expose every single service for receiving requests.

### Traffic distribution
The ingress has a set of rules that allows it to find the right recipient for the corresponding request. These rules are either defined by the subdomain and and the path of the url. 

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

