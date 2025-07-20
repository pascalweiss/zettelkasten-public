---
created: 2024-11-03T11:37
updated: 2025-07-19T15:04
---
#public
Stores a piece of information in the cluster, such as a database password in base64. Note that the information is not encrypted, since base64 can easily be decoded. E.g. with
```bash
echo "<my-base64-secret>" | base64 -d
```

For encrypting the secret, use [[K8s - Sealed-Secret]].

### Example manifest
This a secret with docker configuration that I use for accessing my locally deployed nexus from inside the cluster. In this case, I use it for pulling the image and helm chart of my [[My digital garden]]

```yaml
apiVersion: v1
kind: Secret
metadata:
	name: nexus-credentials
	namespace: digital-garden
data:
	.dockerconfigjson: <BASE64-encoded-credentials>	
type: kubernetes.io/dockerconfigjson
```
It can then be applied in the following release manifest

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2beta1
kind: HelmRelease
metadata:
	name: digital-garden
	namespace: digital-garden
spec:
	interval: 5m
	chart:
	spec:
		chart: digital-garden
		version: '0.1.12'
		sourceRef:
			kind: HelmRepository
			name: nexus
			namespace: digital-garden
	values:
		image:
			pullPolicy: Always
		imagePullSecrets:
			- name: nexus-credentials
```

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

