#public

To observe changes in the git (see [[Version Control - Git]]) or helm-releases (see [[Helm]]), The Flux components need to be deployed in the cluster. The following tutorial describes how to do this. 

**Result:**
Flux components are deployed in the cluster. The system is integrated with your git repo and watches it for applying changes.

### Tutorial

source: https://fluxcd.io/flux/installation/bootstrap/github/

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

Go to Github again and create a personal access token according to the flux documenation.

Copy the value of the token.
Export the token value as follows:
```
export GITLAB_TOKEN=#token value
```

Use the following command to **bootstrap** the cluster:
```
flux bootstrap gitlab --owner=abohmeed --repository=myfluxrepo --branch=main --path=clusters/my-cluster --token-auth --personal
```

Flux has now a reference to the git repository for applying changes to the deployment. This git repo get shown as follows:
```
kubectl get gitrepositories.source.toolkit.fluxcd.io -n flux-system
```

### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

