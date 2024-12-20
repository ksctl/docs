---
title: ksctl_create-cluster_civo
description: Command documentation for ksctl_create-cluster_civo
---

## ksctl create-cluster civo

Use to create a Civo managed k3s cluster

### Synopsis

Ksctl ascii [logo]

```
ksctl create-cluster civo [flags]
```

### Examples

```

ksctl create-cluster civo --name demo --region LON1 --storage store-local --nodeSizeMP g4s.kube.small --noMP 3

```

### Options

```
      --bootstrap string       Kubernetes Bootstrap
      --cni string             CNI
      --feature-flags string   Experimental Features: Supported values with comma seperated: [autoscale]
  -h, --help                   help for civo
  -n, --name string            Cluster Name (default "demo")
      --noMP int               Number of Managed Nodes (default -1)
      --nodeSizeMP string      Node size of managed cluster nodes
  -r, --region string          Region
  -s, --storage string         storage provider
  -v, --verbose int            for verbose output
      --version string         Kubernetes Version
  -y, --yes                    approval to avoid showMsg (default true)
```

### SEE ALSO

* [ksctl create-cluster](ksctl_create-cluster.md)	 - Use to create a cluster

###### Auto generated by spf13/cobra on 2-Dec-2024
