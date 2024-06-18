---
title: K3s
description: K3s Kubernetes Distributions
tags: [k3s, ha, core]
categories: [Kubernetes Provider]
---

{{% pageinfo %}}
K3s for HA Cluster on supported provider
{{% /pageinfo %}}

K3s is used for self-managed clusters. Its a lightweight k8s distribution.
We are using it as follows:
* controlplane (k3s server)
* workerplane (k3s agent)
* datastore (etcd members)

{{% alert color= "info" title="Info" %}}
Here the Default CNI is flannel
{{% /alert %}}

