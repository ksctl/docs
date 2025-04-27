---
title: Cilium
description: Cilium CNI
tags: [core]
---

{{% pageinfo %}}
**Cilium** is a CNI plugin for Kubernetes that provides advanced networking and security features. It uses eBPF (extended Berkeley Packet Filter) technology to enable high-performance networking, load balancing, and security policies at the kernel level.
{{% /pageinfo %}}


{{% alert color= "info" title="Note" %}}
This Docs is only Cilium provided by Ksctl

You can only choose CNI plugin during the cluster creation process.
{{% /alert %}}

## Version selection

Default: `latest`

Now you can choose the Cilium version you want to install.

![](/img/cni-addon-ver.png)

## Cilium configuration

You can customize the Cilium Configuration. 3 modes are available:
1. **Default**: It represents opinionated configuration for Cilium by Ksctl Team.
```yaml {linenos=inline hl_lines=["1-14","16-17", "19-21", "23-29"]}
hubble:
  ui:
    enabled: true
  relay:
    enabled: true
  metrics:
    enabled:
      - dns
      - drop
      - tcp
      - flow
      - port-distribution
      - icmp
      - httpV2:exemplars=true;labelsContext=source_ip,source_namespace,source_workload,destination_ip,destination_namespace,destination_workload,traffic_direction

l7Proxy: true
kubeProxyReplacement: true

encryption:
  enabled: true
  type: wireguard

operator:
  replicas: 3
  prometheus:
    enabled: true

prometheus:
  enabled: true
```
2. **Advance**: You can specify the helm chart `values.yml` file to customize the Cilium configuration. it will open a text editor based on your terminal ENV `$EDITOR` if not set it will use `vim` as default. [Refer Helm Chart Values](https://artifacthub.io/packages/helm/cilium/cilium?modal=values-schema) ![](/img/cni-addon-other-modes.png)
3. **Guided**: It will provide you our preconfigured options of what all specific omponents to Enable/Disable ![](/img/cni-addon-guided.png)
