---
title: Concepts
description: >
  Concepts around ksctl core
---

{{% pageinfo %}}
This section will help you to learn about the underlying system of Ksctl. It will help you to obtain a deeper understanding of how Ksctl works.
{{% /pageinfo %}}

## 📐 Architecture
Here is the entire Ksctl system level design
![](/img/ksctl_solution.svg)

## Sequence diagrams for 2 major operations

### Create Cloud-Managed Clusters
```mermaid
sequenceDiagram
    participant cm as Manager Cluster Managed
    participant cc as Provision Controller
    cm->>cc: transfers specs from user or machine
    cc->>cc: to create the cloud infra (network, subnet, firewall, cluster)
    cc->>cm: 'kubeconfig' and other cluster access to the state
    cc->>cm: status of creation
```

### Create Self-Managed HA clusters
```mermaid
sequenceDiagram
    participant csm as Manager Cluster Self-Managed
    participant cc as Provision Controller
    participant bc as Bootstrap Controller
    csm->>cc: transfers specs from user or machine
    cc->>cc: to create the cloud infra (network, subnet, firewall, vms)
    cc->>csm: return state to be used by BootstrapController
    csm->>bc: transfers infra state like ssh key, pub IPs, etc
    bc->>bc: bootstrap the infra by either (k3s or kubeadm)
    bc->>csm: 'kubeconfig' and other cluster access to the state
    bc->>csm: status of creation
```
