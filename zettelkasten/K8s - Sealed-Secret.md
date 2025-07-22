---
created: 2025-06-11T09:17
updated: 2025-07-19T15:50
---
#public

Secrets have the problem that they are not encrypted. They are just encoded in base64. If e.g. the secret is part in a public git repository, then the secret information is open to everyone. 
A sealed secret solves this problem, by encrypting the secret information with a public key, provided by a `sealed-secret-controller`, which must be deployed in the cluster. The `sealed-secret-controller` then decrypts the sealed secret inside the cluster with its private key.

This is a tutorial on how to create a sealed secret from a normal [[K8s - Secret]]

### Prerequisites
- Install the `sealed-secret-controller` helm chart in the cluster. 
- Install the cli `kubeseal`
Since I use the gitops way, I followed this tutorial: https://fluxcd.io/flux/guides/sealed-secrets/

### How to get the public sealing key
The tutorial above suggests to utilize the ability of `kubeseal` to automatically retrieve the public key. This didn't work in my case, because the `sealed-secret-controller` lies in the namespace `flux-system` namespace. I solved this by following this suggestion: https://github.com/bitnami-labs/sealed-secrets/issues/368#issuecomment-1646192551

Long story short, load the public key manually:
```bash
kubectl get secret \
	--namespace flux-system \
	--selector sealedsecrets.bitnami.com/sealed-secrets-key=active \
	--output jsonpath='{.items[0].data.tls\.crt}' \
	| base64 -d > ./sealing-key.pem
```

### How to create a sealed secret 
Say we have a [[K8s - Secret]], you can create a sealed secret from it with 
```bash
kubeseal \
	--cert=./sealing-key.pem \
	--format yaml \
	< <original-secret-manifest>.yaml \
	> <RESULTING-SEALEE-SECRET.yaml>
```
Note that it applies the sealing-key, created above. 

### Related links
- https://youtu.be/wWMJCY2E0d4?si=p8QPJmPIl0XopY3x


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

