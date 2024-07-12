---
title: Ksctl State-Importer
description: Documentation on ksctl stateimporter
categories: [Examples, Placeholders]
tags: [docs]
---

{{% pageinfo %}}
It is a helper deployment to transfer state information from one storage option to another.
{{% /pageinfo %}}

It is used to transfer data in `~/.ksctl` location (provided the cluster is created via `storageProvider: store-local`).


It utilizes the these 2 methods:
- `Export`: [StorageFactory Interface](https://github.com/ksctl/ksctl/blob/d3c2d74fe03ab1e8ad48d45290662c878196889b/pkg/types/typesStorage.go#L34)
- `Import`: [StorageFactory Interface](https://github.com/ksctl/ksctl/blob/d3c2d74fe03ab1e8ad48d45290662c878196889b/pkg/types/typesStorage.go#L37)

so before the ksctl agent is deployed we first create this pod which in turn runs a http server having `storageProvider: store-kubernetes` and uses `storage.Import()` method

once we get 200 OK responses from the http server we remove the pod and move to ksctl agent deployment so that it can use the state file present in configmaps, secrets

{{% alert title="Warning" color="warning" %}}
If the storageType is external (mongodb), we don't need this to be happening instead we create kubernetes secret where the external storage solution environment variable is set and also we need to customize the ksctl agent deployment
{{% /alert %}}