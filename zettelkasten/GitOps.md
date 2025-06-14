---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public
A paradigm, that places git at the heart of building and deploying software. Here, git (see [[Version Control - Git]]) is the only source of truth. 

### Benefits
- Version Control: Everything is versioned, and can be rolled back, easily
- Collaboration: Developers and operators can collaborate more easily
- Automation: It enables automated and consistent deployments

### Core Principles
- **Declarative configuration**: Everything is declared in a config file (e.g. yaml)
- **Version control**: All configurations should be stored in a git repository
- **Automated synchronisation**: The actual state should be synchronised with the current state in git
- **Observability**: Changes and current state should be easily observable

### Related links
- GitOps can be achieved with [[FluxCD]]


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

