---
created: 2025-03-12T17:54
updated: 2025-06-14T21:38
---
#public

**With my homelab, I want to: ...**
- ... deploy everything in a kubernetes cluster
- ... use gitlab for version control and CI/CD pipelines
- ... have gitlab running outside the kubernetes cluster
- ... have gitlab runners running inside the kubernetes cluster
- ... have one repository for the infrastructure
- ... have a single (main) domain, …
   - ... with which everything can be accessed ...
   - ... that is from a public domain provider, so that I can have ssl certificates for https

**for each application, I want to: ...**
- ... have a separate repository ...
- ... where I have a main branch ...
- ... where I create feature branches ...
- ... where I want to implement new features
- **for each branch in the corresponding repository, I want to: ...**
	- ... be able to create MRs for new features, in which a CI/CD pipeline runs ...
	- ... that triggers a new preview deployment for the new feature in kubernetes
- **for each deployment, I want to: ...**
	- ... have a separate namespace
	- ... have a separate separate subdomain (to) the main domain)


**So that: ...**
- ... for every application and the corresponding main-branch, there is a main-namespace, such as: `app1`, `app2`
- ... for every main-namespace, there is a subdomain, such as: `app1.homelab.lan`, `app2.homelab.lan`, etc.
- ... for every application and every feature branch, there is a separate  feature-namespace, such as: `app1_feature1`, `app1_feature2`, `app2_feature1`, etc.
- ... for every feature-namespace, there is a feature subdomain, such as: `app1.feature1.homelab.lan`, `app1.feature2.homelab.lan`, etc.



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

