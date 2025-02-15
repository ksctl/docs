---
title: Azure
description: >
  Azure Cloud Provider
categories: [Cloud Provider]
tags: [azure, ha, managed, core]
---

{{% pageinfo %}}
Azure support for Self-Managed and Managed Kubernetes Clusters
{{% /pageinfo %}}

{{% alert color="warning" title="Caution" %}}
Azure credentials are required to access clusters. These credentials are sensitive information and must be kept secure.
{{% /alert %}}

## Azure Credential Requirements

### Subscription ID
Your Azure subscription identifier can be found in your subscription details.

![azure-subscription](/img/azure/azure-subs-id.png)

### Tenant ID
Located in the Azure Dashboard, which provides access to all required credentials.

![azure-dashboard](/img/azure/azure-dashboard.png)

To locate your Tenant ID:

![](/img/azure/azure-tenantid.png)

### Client ID (Application ID)
Represents the identifier of your registered application.

Steps to create:
1. Navigate to App Registrations

![](/img/azure/azure-app-reg.png)

2. Register a new application
![](/img/azure/azure-create-app-reg.png)

3. Obtain the Client ID
![](/img/azure/azure-clientid.png)

### Client Secret
Authentication key for your registered application.

Steps to generate:
1. Access secret creation
![create app secret](/img/azure/azure-client-secret1.png)

2. Configure secret settings
![after-click](/img/azure/azure-client-secret.png)

3. Save the generated secret
![copy-secret](/img/azure/azure-client-secret2.png)

### Role Assignment
Configure application permissions:

1. Navigate to Subscriptions > Access Control (IAM)
2. Select "Role Assignment"
3. Click "Add > Add Role Assignment"
4. Create new role and specify the application name
5. Configure desired permissions

![role-assign-app](/img/azure/azure-role-app.png)

## Authentication Methods

### Command Line Interface
```bash
ksctl configure cloud
```

## Available Cluster Types

### Self-Managed Clusters
Self-managed clusters with the following components:
- Distributed etcd database instances
- HAProxy load balancer for control plane high availability
- Multiple control plane nodes
- Worker nodes

Bootstrap options:
- k3s (lightweight Kubernetes distribution)
- kubeadm (official Kubernetes bootstrap tool)

### Azure Kubernetes Service (AKS)
Fully managed Kubernetes service by Azure.

## Cluster Management Features

{{% alert title="Cluster Operations" %}}

### Managed Clusters (AKS)
- Create and delete operations
- Cluster switching
- Infrastructure updates currently not supported

### High Availability Clusters
- Worker node scaling (add/remove)
- Secure SSH access to all components:
  - Database nodes
  - Load balancer
  - Control plane nodes
  - Worker nodes
- Protected by SSH key authentication
- Public access enabled

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
