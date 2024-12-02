---
title: ksctl_create-cluster_ha-civo
description: Command documentation for ksctl_create-cluster_ha-civo
---

## ksctl create-cluster ha-civo

Use to create a self-managed Highly Available cluster on Civo

### Synopsis

Ksctl ascii [logo]

```
ksctl create-cluster ha-civo [flags]
```

### Examples

```

ksctl create-cluster ha-civo --name demo --region LON1 --bootstrap k3s --storage store-local --nodeSizeCP g3.small --nodeSizeWP g3.medium --nodeSizeLB g3.small --nodeSizeDS g3.small --noWP 1 --noCP 3 --noDS 3
ksctl create-cluster ha-civo --name demo --region LON1 --bootstrap kubeadm --storage store-local --nodeSizeCP g3.medium --nodeSizeWP g3.large --nodeSizeLB g3.small --nodeSizeDS g3.small --noWP 1 --noCP 3 --noDS 3 --cni cilium@v1.16.1

```

### Options

```
      --bootstrap string       Kubernetes Bootstrap
      --cni string             CNI
      --feature-flags string   Experimental Features: Supported values with comma seperated: [autoscale]
  -h, --help                   help for ha-civo
  -n, --name string            Cluster Name (default "demo")
      --noCP int               Number of ControlPlane Nodes (default -1)
      --noDS int               Number of DataStore Nodes (default -1)
      --noWP int               Number of WorkerPlane Nodes (default -1)
      --nodeSizeCP string      Node size of self-managed controlplane nodes
      --nodeSizeDS string      Node size of self-managed datastore nodes
      --nodeSizeLB string      Node size of self-managed loadbalancer node
      --nodeSizeWP string      Node size of self-managed workerplane nodes
  -r, --region string          Region
  -s, --storage string         storage provider
  -v, --verbose int            for verbose output
      --version string         Kubernetes Version
  -y, --yes                    approval to avoid showMsg (default true)
```

### SEE ALSO

* [ksctl create-cluster](ksctl_create-cluster.md)	 - Use to create a cluster
* [ksctl create-cluster ha-civo add-nodes](ksctl_create-cluster_ha-civo_add-nodes.md)	 - Use to add more worker nodes in self-managed Highly-Available cluster on Civo

###### Auto generated by spf13/cobra on 1-Dec-2024