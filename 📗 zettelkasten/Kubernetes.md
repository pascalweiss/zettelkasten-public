---
created: 2024-10-09T08:36
updated: 2025-06-11T09:17
---

Kubernetes (K8s) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. Think of it as an operating system for the cloud, abstracting away the underlying infrastructure and providing a consistent environment across different clouds and on-premises deployments.


For complete reference: [Kubernetes Documentation](https://kubernetes.io/docs/reference/glossary/?fundamental=true)

## Core Components

### Cluster Architecture

#### Nodes

Nodes are the physical or virtual machines that form the foundation of a Kubernetes cluster. They provide the compute resources (CPU, memory, storage) necessary to run containerized applications.

- **Types of Nodes:**
    - **Worker Nodes**: Run application workloads as containers
    - **Master Nodes**: Control plane components that manage the cluster

#### Control Plane (Master)

The Control Plane manages the Kubernetes cluster and consists of several components:

- **API Server**: Entry point for all REST commands to the cluster
- **etcd**: Distributed key-value store that stores all cluster data
- **Scheduler**: Assigns newly created pods to nodes
- **Controller Manager**: Runs controller processes (e.g., node controller, replication controller)
- **Cloud Controller Manager**: Integrates with underlying cloud provider APIs

#### Worker Nodes

Worker nodes host the applications as containers and include:

- **kubelet**: Agent that ensures containers are running in a pod
- **kube-proxy**: Network proxy that maintains network rules
- **Container Runtime**: Software responsible for running containers (e.g., containerd, CRI-O)

### Workload Resources

#### Pods

The smallest deployable unit in Kubernetes, consisting of one or more containers that share storage and network resources.

#### Deployments

Provide declarative updates for Pods and ReplicaSets, enabling rolling updates, rollbacks, and scaling.

#### StatefulSets

Manage stateful applications, providing unique network identities, stable persistent storage, and ordered deployment and scaling.

#### ReplicaSets

Ensure a specified number of pod replicas are running at any given time.

#### DaemonSets

Ensure all (or some) nodes run a copy of a specific pod, useful for cluster-wide services like monitoring or logging.

### Storage

#### Volumes

Provide persistent storage for Pods that persists beyond container restarts.

#### Persistent Volumes (PV)

Cluster resources provisioned by administrators that provide storage.

#### Persistent Volume Claims (PVC)

Requests for storage by users that can be fulfilled by Persistent Volumes.

### Networking

#### Services

Abstract way to expose an application running on a set of Pods as a network service.

- **ClusterIP**: Exposes the service on an internal IP within the cluster
- **NodePort**: Exposes the service on each node's IP at a static port
- **LoadBalancer**: Exposes the service externally using a cloud provider's load balancer
- **ExternalName**: Maps a service to a DNS name

#### Ingress

API object that manages external access to services in a cluster, typically HTTP/HTTPS routes.

### Configuration

#### ConfigMaps

Store non-confidential configuration data as key-value pairs.

#### Secrets

Store sensitive information such as passwords, OAuth tokens, and SSH keys. See [[Secret]] and [[Sealed-Secret]]

### Namespaces

Virtual clusters within a physical cluster that provide a scope for names and enable resource isolation.

## Kubernetes Manifests

Kubernetes resources are defined using YAML or JSON manifests that specify the desired state of the cluster. A basic Pod manifest example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  namespace: default
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

## Ecosystem Tools

### Package Management

- **Helm**: Package manager for Kubernetes that simplifies deploying and managing applications
- **Kustomize**: Template-free way to customize application configuration

### GitOps

- **FluxCD**: Tool that ensures the state of a cluster matches the configuration in Git
- **ArgoCD**: Declarative, GitOps continuous delivery tool for Kubernetes

### Service Mesh

- **Istio**: Provides traffic management, security, and observability
- **Linkerd**: Lightweight service mesh focused on simplicity and performance

### Monitoring & Logging

- **Prometheus**: Monitoring and alerting toolkit
- **Grafana**: Visualization and analytics platform
- **Elastic Stack**: Logging and analysis suite


### Backlinks
```dataview 
list from [[#]] where contains(file.outlinks, this.file.link)
```

