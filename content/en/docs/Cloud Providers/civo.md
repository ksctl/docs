---
title: Civo
description: >
  Civo Cloud Provider
categories: [Cloud Provider]
tags: [civo, ha, managed, core]
---

{{% pageinfo %}}
Civo support for High Availability and Managed Kubernetes Clusters
{{% /pageinfo %}}

{{% alert color="warning" title="Caution" %}}
Civo API credentials are required to access clusters. These credentials are sensitive information and must be kept secure.
{{% /alert %}}

## Obtaining Civo Credentials

### 1. Access API Settings
Navigate to your Civo dashboard settings:

![](/img/civo/civo-settings.png)

### 2. Open Profile Settings
Select your profile section:

![](/img/civo/profile.png)

### 3. Generate API Key
Access the API keys section and create or copy your API token:

![](/img/civo/security-api.png)

## Authentication Methods

### Environment Variables
Set your Civo API token:
```bash
export CIVO_TOKEN=""
```

### Command Line Interface
Use the ksctl credential manager:
```bash
ksctl cred
```

## Available Cluster Types

### High Availability (HA) Clusters
Self-managed clusters with the following components:
- Distributed etcd database instances
- HAProxy load balancer for control plane high availability
- Multiple control plane nodes
- Worker nodes

Bootstrap options:
- k3s (lightweight Kubernetes distribution)
- kubeadm (official Kubernetes bootstrap tool)

### Civo Kubernetes Service (CKS)
Fully managed Kubernetes service by Civo.

## Cluster Management Features

{{% alert title="Cluster Operations" %}}

### Managed Clusters (CKS)
- Cluster creation and deletion
- Cluster switching capability
- Infrastructure updates currently not supported

### High Availability Clusters
#### Node Management
- Dynamic worker node scaling (add/remove nodes)
- Secure SSH access to cluster components

#### Access Control
- **Control Plane Components**
  - Database nodes (Public access)
  - Load balancer (Public access)
  - Control plane nodes (Public access)
  - All secured with SSH key authentication

- **Worker Nodes**
  - Private network access only
  - SSH access via internal network
  - Protected by SSH key authentication

{{% /alert %}}


## Looking for CLI Commands?

All CLI commands mentioned in this documentation have detailed explanations in our command reference guide.

{{% alert title="CLI Reference" %}}
👉 Check out our comprehensive [CLI Commands Reference](/docs/develop/reference/) for:
- Detailed command syntax
- Usage examples
- Available options and flags
- Common use cases
{{% /alert %}}
