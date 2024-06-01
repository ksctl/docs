---
title: Ksctl Components
description: Place of all the documentation for the Operators used specifically for k8s clusters
tags: [docs]
---

## Components
- ksctl agent
- ksctl stateimporter
- ksctl application controller

## Sequence diagram on how its deployed
```mermaid
flowchart TD
Base(Ksctl Infra and Bootstrap) -->|Cluster is created| KC(Ksctl controller)
KC -->|Creates| Storage{storageProvider=='local'}
Storage -->|Yes| KSI(Ksctl Storage Importer)
Storage -->|No| KA(Ksctl Agent)
KSI -->KA
KA -->|Health| D(Deploy other ksctl controllers)
```

{{% alert title="Some Docs" color="primary" %}}
Here is the new event driven architecture Diagram
![Diagram](https://raw.githubusercontent.com/ksctl/enhancements/main/poc/ksctl-components/overall.svg)

For more information about this
[Refer](https://github.com/ksctl/enhancements/tree/main/poc/ksctl-components)

{{% /alert %}}
