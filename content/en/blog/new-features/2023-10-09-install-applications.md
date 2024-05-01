---
title: Feature Install Applications
tags: [kubernetes-client-go, ksctl, cncf]
author: Dipankar Das ([@DipankarDas011](https://twitter.com/DipankarDas011))

---

> **DEPRECATED**

{{% alert title="Note `Experimental`" %}}
Currently Argocd, Kube-Prometheus Stack, Cilium ... is supported
{{% /alert %}}

## How to use it
It provides a way to install common applications like argocd, and many more to come

> it is supported for both managed and HA cluster

```bash
ksctl create <cloud-provider> ...  --feature-flag application --apps argocd,istio --cni cilium
```

## For the apps options are

---
Updated: 2023-12-30
---

- argo-rollouts
- argocd
- istio
- prometheus-stack

## for the cni

- cilium
- azure -> for aks
- flannel (default) -> for ha default in k3s so no need
- kubenet
- kind
