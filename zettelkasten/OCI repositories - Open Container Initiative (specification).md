#public
- Used to distribute container images and helm charts over the network
- Is an alternative to distribution via pure http repositories (like [[ChartMuseum]])
- Distributes resources via the `oci://` protocol
- Offers artifact signing and vulnerability scanning

### digest references
A digest is a hash that was created based on the image or the helm chart. It can be used for validating the exact contend of the artifact. Hence it guarantees that the resource was not manipulated. A digest reference may look as follows: 
```
my-chart@sha256:duh284dh…
```


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

