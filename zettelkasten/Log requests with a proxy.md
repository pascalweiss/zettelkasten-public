---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
To observe the outgoing requests of an application, you may install a proxy behind it. This proxy logs every incoming request and forwards them to the original recipient. 

In contrast to the fake server, described in [[log outgoing requests with a fake server]], it doesn't break the observed system. 
### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

