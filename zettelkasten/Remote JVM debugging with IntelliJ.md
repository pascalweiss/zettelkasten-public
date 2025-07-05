---
created: 2025-03-03T09:56
updated: 2025-07-04T18:36
---
#draft

### Application setup

#### remote - k8s
In k8s cluster update the run configuration in the configmap so that the debugging port is opened (here port 8000)
```yaml
...
containers: 
- command: 
	- java 
	- -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=8000 
	- org.springframework.boot.loader.launch.JarLauncher 
  env:
...
```
The application should then restart. From my experience, the debugging port is then logged. 

#### port forwarding
The final step for the application configuration is to forward the debugging port to the localhost. This port is usually inaccessible from outside the cluster, but once forwarded, it can be accessed by the IDE (see the next step).

### IntelliJ run configuration
IntelliJ provides a run configuration for remote debugging. Here, the port must be configured. See screenshot.

Done ✅ 

![[Pasted image 20250303100553.png]]

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

