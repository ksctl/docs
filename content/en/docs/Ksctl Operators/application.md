---
title: Ksctl Application Controller
description: Documentation on ksctl application controller
categories: [Examples, Placeholders]
tags: [docs]
---

{{% pageinfo %}}
It helps in deploying applications using crd to help manage with installaztion, upgrades, downgrades, uninstallaztion. from one version to another and provide a single place of truth where to look for which applications are installed
{{% /pageinfo %}}

## Types

### Stack

For defining a hetrogenous components we came up with a stack which contains `M` number of components which are different applications with their versions

{{% alert title="Info" color="info" %}}
this is current available on all clusters created by `ksctl@v1.2.0`
{{% /alert %}}

{{% alert title="Note" color="info" %}}
It has a dependency on `ksctl agent`
{{% /alert %}}

### Supported Apps and CNI
| Name | Type | Category
|- | - | - |
| Argo-CD | App | CI/CD |
| Argo-Rollouts | App | CI/CD |
| Istio | App | Service Mesh |
| Cilium | Cni | - |
| Flannel | Cni | - |
| Kube-Prometheus | App | Monitoring |

#### Example usage

Lets deploy `argocd@v2.9.X`, `prometheus-stack@v55.X.Y`
```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: monitoring-plus-gitops
spec:
  components:
    - appName: argocd
      appType: app
      version: v2.9.12

    - appName: prometheus-stack
      appType: app
      version: "55.0.0"
```

You can see once its deployed it fetch and deploys them

Lets try to upgrade them to their latest versions
```bash
kubeclt edit stack monitoring-plus-gitops
```

```yaml
apiVersion: application.ksctl.com/v1alpha1
kind: Stack
metadata:
  name: monitoring-plus-gitops
spec:
  components:
    - appName: argocd
      appType: app
      version: latest

    - appName: prometheus-stack
      appType: app
      version: latest
```

once edited it will uninstall the previous install and reinstalls the latest deployments
