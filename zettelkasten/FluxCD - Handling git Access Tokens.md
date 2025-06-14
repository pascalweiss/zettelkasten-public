---
created: 2025-03-03T08:00
updated: 2025-06-14T21:38
---
#public

The token might expire over time. Don't forget to update it


With the bootstrapping (see [[FluxCD - Bootstrapping with Gitlab]]), flux stores the access token in a **kubernetes secret**, see:
```
kubectl get secrets -n flux-system
```

To reveal the token, execute:
```
kubectl get secret flux-system -n flux-system -o jsonpath='{.data.password}' | base64 -d
```



### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

