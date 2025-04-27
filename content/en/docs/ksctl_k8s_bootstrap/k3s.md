---
title: K3s
description: K3s Kubernetes Distribution
tags: [k3s, ha, core]
categories: [Kubernetes Provider]
---

{{% pageinfo %}}
K3s for self-managed Cluster on supported cloud providers
{{% /pageinfo %}}

## Overview

K3s is a lightweight, certified Kubernetes distribution designed for resource-constrained environments. In ksctl, K3s is used for creating self-managed Kubernetes clusters with the following components:

* **Control plane** (k3s server) - Manages the Kubernetes API server, scheduler, and controller manager
* **Worker plane** (k3s agent) - Runs your workloads
* **Datastore** (external etcd) - Manages cluster state
* **Load balancer** - Distributes API server traffic in HA deployments

## Architecture

ksctl deploys K3s in a high-availability configuration with:

- Multiple control plane nodes for redundancy
- External etcd cluster for reliable data storage
- Load balancer for API server access
- Worker nodes for running applications

## CNI Options

K3s in ksctl supports the following Container Network Interface (CNI) options:

* **Flannel** (default) - Simple overlay network provided by K3s
* **None** - Disables the built-in CNI, allowing for installation of external CNIs like Cilium

{{% alert color="info" title="Default CNI" %}}
The default CNI for K3s in ksctl is Flannel.
{{% /alert %}}

To use an external CNI, select "none" during cluster creation. This will:
- Disable the built-in Flannel CNI
- Set `--flannel-backend=none` and `--disable-network-policy` flags
- Allow you to install your preferred CNI solution

## Version Selection

ksctl allows you to choose specific K3s versions for your cluster. The tool validates versions against available releases from the K3s GitHub repository.

![](/img/k3s-ver.png)

If no version is specified, ksctl will automatically use the latest stable K3s release.

## Control Plane Configuration

The K3s control plane in ksctl is deployed with the following optimizations:

- Node taints to prevent workloads from running on control plane nodes
- TLS configuration with certificates for secure communication
- Integration with the external etcd datastore
- Configuration for high-availability when multiple control plane nodes are deployed

## Advanced Features

K3s in ksctl includes several advanced features:

- **HA Setup**: Multiple control plane nodes with an external etcd datastore
- **Kubeconfig Management**: Automatic configuration of kubeconfig with the correct cluster endpoints
- **Certificate Management**: Secure TLS setup with certificate generation
- **Seamless Scaling**: Easy addition of worker nodes to the cluster

## Limitations

- K3s in ksctl is designed for self-managed clusters only
- Some K3s-specific features may require additional manual configuration

## Next Steps

After deploying a K3s cluster with ksctl, you can:

1. Access your cluster using the generated kubeconfig
2. Install additional components using Kubernetes package managers
3. Deploy your applications using kubectl, Helm, or other tools
4. Scale your cluster by adding more worker nodes as needed
