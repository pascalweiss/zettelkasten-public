---
created: 2025-03-11T22:32
updated: 2025-06-14T21:20
---
#public

This page describes how to mirror commits from a gitlab repository to a github repository.

#### On GitHub
- Go to github account settings > developer settings > personal access tokens
- Create a PAT (private access token) that allows to push to the corresponding repository

#### On Gitlab
- Got to Settings > Repository > Mirroring Repositories >> add new
- paste the https-address of the github repo
- select mirror-direction: push
- select authentication: Username & Password
- provide github username 
- provide PAT from github as password
- select "keep divergent refs"
- ok 

--> done

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

