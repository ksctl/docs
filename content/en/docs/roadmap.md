---
title: Roadmap
description: What does your user need to know to try your project?
tags: [roadmap, core]
---

{{% pageinfo %}}
Current Status on Supported Providers and Next Features
{{% /pageinfo %}}

### Supported Providers

<div class="-text-green">Done</div>
<div class="-text-red">Not Started</div>
<div class="-text-black">No Plans</div>
<div class="-text-blue">Backlog</div>

```mermaid
flowchart LR;
  classDef green color:#022e1f,fill:#00f500;
  classDef red color:#022e1f,fill:#f11111;
  classDef white color:#022e1f,fill:#fff;
  classDef black color:#fff,fill:#000;
  classDef blue color:#fff,fill:#00f;

  XX[ksctl]--CloudFactory-->web{Cloud Providers};
  XX[ksctl]--DistroFactory-->web2{Distributions};
  XX[ksctl]--StorageFactory-->web3{State Storage};

  web--Civo-->civo{Types};
  civo:::green--managed-->civom[Create & Delete]:::green;
  civo--HA-->civoha[Create & Delete]:::green;

  web--Local-Kind-->local{Types};
  local:::green--managed-->localm[Create & Delete]:::green;
  local--HA-->localha[Create & Delete]:::black;

  web--AWS-->aws{Types};
  aws:::green--managed-->awsm[Create & Delete]:::green;
  aws--HA-->awsha[Create & Delete]:::green;

  web--Azure-->az{Types};
  az:::green--managed-->azsm[Create & Delete]:::green;
  az--HA-->azha[Create & Delete]:::green;

  web2--K3S-->k3s{Types};
  k3s:::green--HA-->k3ha[Create & Delete]:::green;

  web2--Kubeadm-->kubeadm{Types};
  kubeadm:::green--HA-->kubeadmha[Create & Delete]:::green;

  web3--Local-Store-->slocal{Local}:::green;
  web3--Remote-Store-->rlocal{Remote}:::green;
  rlocal--Provider-->mongo[MongoDB]:::green;

```

### Next Features

- Talos as the next Bootstrap provider
- Green software which can help you save energy and also better somehow
- WASM first class support feature
- ML features unikernels and better ML workload scalability
- Production stack for monitoring, security, to application specific application integrations like vault, kafka, etc.
- Health checks of various k8s cluster
- Role Based Access Control for any cluster
- Ability import any existing cluster and also to respect the existing state and not overwrite it with the new state from ksctl but to be able to manage only the resources which the tool has access
- add initial production ready for cert manager + ingress controller (nginx) + gateway api
- add initial production ready for monitoring (prometheus + grafana) tracing (jaeger) Opentelemtery support
- add initial production ready for Networking (cilium)
- add initial production ready for service mesh (istio)


