---
created: 2025-03-03T08:00
updated: 2025-06-12T17:49
---
#public

To observe changes in the git (see [[Version Control - Git]]) or helm-releases (see [[Helm]]), The Flux components need to be deployed in the cluster. The following tutorial describes how to do this. 

**Result:**
Flux components are deployed in the cluster. The system is integrated with your git repo and watches it for applying changes.

### Tutorial

source: https://fluxcd.io/flux/installation/bootstrap/gitlab/

To get started, it is required to deploy the flux system in a dedicated namespace. The basic steps are:

```bash
brew install fluxcd/tap/flux
```

Type the following commands to create the necessary directory structure (source: https://fluxcd.io/flux/installation/configuration/boostrap-customization/):
```
cd myfluxrepo
mkdir -p clusters/my-cluster/flux-system
cd clusters/my-cluster/flux-system
touch gotk-components.yaml gotk-sync.yaml kustomization.yaml
```

Add the following to the kustomization.yaml file:
```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
  - gotk-components.yaml
  - gotk-sync.yaml
```

Go to gitlab again and create a personal access token (PAT) according to the flux documenation. It will require full api access. 

Copy the value of the token.
Export the token value as follows:

```bash
export GITLAB_TOKEN=<token-value>. # full api token
```

Use the following command to **bootstrap** the cluster:

```sh
flux bootstrap gitlab \
  --deploy-token-auth \ # alternative --token-auth
  --owner=my-gitlab-username \
  --repository=my-project \
  --branch=master \
  --path=clusters/my-cluster \
  --personal./
```



##### param desc
- `--deploy-token-auth`: will use the the PAT to make changes to the repo once, afterwards it'll store a readonly token in the cluster
- `token-auth`: will store the PAT continuously in the cluster. Will enable features like image-automation or auto-version-bumps
- `--owner=my-gitlab-username`: Specifies the GitLab namespace (user or group) where the repository resides.
- `--repository=my-project`: The name of the GitLab repository that will store the Flux configuration.
- `--branch=master`: The Git branch Flux will use for bootstrapping and continuous reconciliation.
- `--path=clusters/my-cluster`: The path within the repository that contains the Kubernetes manifests for this cluster.
- `--personal`: Indicates that the repository is located under a personal GitLab account rather than a group.



Flux has now a reference to the git repository for applying changes to the deployment. This git repo get shown as follows:

```bash
kubectl get gitrepositories.source.toolkit.fluxcd.io -n flux-system
```

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

