---
title: Civo
description: >
  Civo Cloud Provider
categories: [Cloud Provider]
tags: [civo, ha, managed, core]
---

{{% pageinfo %}}
Civo support for HA and Managed Clusters
{{% /pageinfo %}}

{{% alert color="warning" title="Caution" %}}
we need credentials to access clusters

these are confidential information so shouldn't be shared with anyone
{{% /alert %}}


## Getting credentials

### under settings look for the profile
![](/ksctl-docs/img/civo/civo-settings.png)
![](/ksctl-docs/img/civo/profile.png)

### copy the credentials
![](/ksctl-docs/img/civo/security-api.png)

## How to add credentials to ksctl

1. Environment Variables

```bash
export CIVO_TOKEN=""
```

2. Using command line

```bash
ksctl cred
```

## Current Features

### Cluster features
#### Highly Available cluster
clusters which are managed by the user not by cloud provider

> using K3s kubernetes distribution which is lightweight

custom components being used
- MySQL database instance
- HAProxy loadbalancer instance for controlplane nodes
- controlplane instances
- workerplane instances

#### Managed Cluster
clusters which are managed by the cloud provider

### Other capabilities

#### Create, Update, Delete, Switch

{{% alert title="Update the cluster infrastructure" %}}

**Managed cluster**: till now it's not supported

**HA cluster**
- addition and deletion of new workerplane node
- SSH access to each cluster node (DB, LB, Controplane) _Public Access_, secured by private key
- SSH access to each workplane _Private Access_ via local network, secured by private key
{{% /alert %}}

{{% alert color="success" title="Managed Cluster" %}}

<video width="360" height="202" controls>
<source src="/ksctl-docs/videos/ksctl-civo-managed.mp4" type="video/mp4" />
Your browser does not support the video tag.
</video>
{{% /alert %}}


{{% alert color="success" title="Highly Available Cluster" %}}

<video width="360" height="202" controls>
<source src="/ksctl-docs/videos/ksctl-civo-ha.mp4" type="video/mp4" />
Your browser does not support the video tag.
</video>
{{% /alert %}}

