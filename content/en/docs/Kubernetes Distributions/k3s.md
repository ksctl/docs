---
title: K3s
description: K3s Kubernetes Distributions
tags: [k3s, ha, core]
categories: [Kubernetes Provider]
---

K3s for HA Cluster on supported provider

K3s is used for self-managed clusters. Its a lightweight k8s distribution.
We are using it as follows:
* controlplane (k3s server)
* workerplane (k3s agent)
* datastore (etcd members)

{{% alert color= "warning" title="Security" %}}
Currently all VMs require SSH authentication and all ports are open. But in future versions it will be resolved
{{% /alert %}}

{{% alert color= "warning" title="In Progress" %}}
Document available Kubernetes version
{{% /alert %}}
