---
title: ksctl_delete-cluster_civo
description: Command documentation for ksctl_delete-cluster_civo
---

## ksctl delete-cluster civo

Use to delete a Civo managed k3s cluster

### Synopsis

Ksctl ascii [logo]

```
ksctl delete-cluster civo [flags]
```

### Examples

```

ksctl delete civo --name demo --region LON1 --storage store-local

```

### Options

```
      --feature-flags string   Experimental Features: Supported values with comma seperated: [autoscale]
  -h, --help                   help for civo
  -n, --name string            Cluster Name (default "demo")
  -r, --region string          Region
  -s, --storage string         storage provider
  -v, --verbose int            for verbose output
  -y, --yes                    approval to avoid showMsg (default true)
```

### SEE ALSO

* [ksctl delete-cluster](ksctl_delete-cluster.md)	 - Use to delete a cluster

###### Auto generated by spf13/cobra on 2-Dec-2024
