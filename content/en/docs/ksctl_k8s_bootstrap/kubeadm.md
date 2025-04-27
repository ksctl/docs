---
title: Kubeadm
description: Kubeadm Kubernetes Distributions
categories: [Kubernetes Provider]
tags: [Kubeadm, ha, core]
---

{{% pageinfo %}}
Kubeadm for HA Cluster on supported provider
{{% /pageinfo %}}

Kubeadm support is added with etcd as datastore

{{% alert color= "info" title="Info" %}}
Here the Default CNI is none
{{% /alert %}}

## Overview

Kubeadm is a tool built to provide best-practice "fast paths" for creating Kubernetes clusters. ksctl integrates Kubeadm to provision highly-available Kubernetes clusters across your infrastructure.


## Features

- **External etcd topology**: Uses a dedicated etcd cluster for improved reliability
- **HA control plane**: Supports multiple control plane nodes for high availability
- **Seamless cluster expansion**: Easily add worker nodes
- **Automatic certificate management**: Handles all required PKI setup
- **Secure token handling**: Manages bootstrap tokens with automatic renewal

## Architecture

ksctl with Kubeadm creates a cluster with the following components:

- **External etcd cluster**: Dedicated nodes for the etcd database
- **Control plane nodes**: Running the Kubernetes control plane components
- **Worker nodes**: For running your workloads
- **Load balancer**: Provides a single entry point to the control plane

```
┌────────────────┐    ┌────────────────┐    ┌────────────────┐
│                │    │                │    │                │
│  Control Plane │    │  Control Plane │    │  Control Plane │
│                │    │                │    │                │
└────────────────┘    └────────────────┘    └────────────────┘
        │                     │                     │
        └─────────────┬───────┴─────────────┬───────┘
                      │                     │
                      ▼                     ▼
           ┌─────────────────────┐  ┌─────────────────┐
           │                     │  │                 │
           │    Load Balancer    │  │  External etcd  │
           │                     │  │                 │
           └─────────────────────┘  └─────────────────┘
                      │
        ┌─────────────┴───────────┐
        │                         │
        ▼                         ▼
┌────────────────┐      ┌────────────────┐
│                │      │                │
│  Worker Node   │ ...  │  Worker Node   │
│                │      │                │
└────────────────┘      └────────────────┘
```

## Technical Details

### Kubernetes Versions

ksctl supports multiple Kubernetes versions through Kubeadm. The system automatically fetches available versions from the Kubernetes releases, allowing you to choose your preferred version.

{{% alert color="info" title="Default Version" %}}
If you don't specify a version, ksctl will use the latest stable Kubernetes version available.
{{% /alert %}}

![Kubeadm version selection](/img/kubeadm-ver.png)

### Container Runtime

The default container runtime used is `containerd`, which is set up and configured automatically during cluster deployment.

### Network Configuration

Kubeadm in ksctl configures the following networking defaults:
- Pod subnet: `10.244.0.0/16`
- Service subnet: `10.96.0.0/12`
- DNS domain: `cluster.local`

### CNI (Container Network Interface)

{{% alert color="info" title="CNI Configuration" %}}
By default, Kubeadm in ksctl uses `none` as the CNI. You can deploy your preferred CNI solution using ksctl's addon system after cluster creation.
{{% /alert %}}

### Bootstrap Process

The bootstrap process follows these steps:

1. **Control plane initialization**:
   - Generates bootstrap tokens and certificate keys
   - Configures the first control plane node
   - Sets up external etcd connection
   - Initializes the Kubernetes API server

2. **Additional control plane nodes**:
   - Join additional control plane nodes to form an HA cluster
   - Share certificates securely between nodes

3. **Worker node setup**:
   - Install required components (containerd, kubelet, etc.)
   - Join worker nodes to the cluster using bootstrap tokens

## Cluster Access

Once your cluster is created, ksctl automatically configures and saves your `kubeconfig` file with appropriate context names based on your cluster details.

## Limitations

- All nodes must run Ubuntu-based Linux distributions
