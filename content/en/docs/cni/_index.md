---
title: Container Network Interface (CNI)
description: Supported CNI by Ksctl
tags: [cni, addon]
---

{{% pageinfo %}}
**Cilium** and **Flannel** for self managed clusters

For Cloud managed cluster it varies based on the provider.
{{% /pageinfo %}}

## Pre-requisites
You get to choose Ksctl CNI when you choose `none` from the main provider :
- Cloud Managed Cluster Provider (**aks**, **eks**, **kind**) _Or_
- Kubernetes Bootstrap Provider (**k3s**, **kubeadm**)

For example, 
![](/img/cni-addon-0.png)
