---
title: Flannel
description: Flannel CNI
tags: [core]
---

{{% pageinfo %}}
**Flannel** is a CNI plugin for Kubernetes that provides a simple and efficient way to manage networking between containers. It creates an overlay network that allows containers to communicate with each other across different hosts, making it easier to deploy and scale applications in a Kubernetes cluster.
{{% /pageinfo %}}


{{% alert color= "info" title="Note" %}}
This Docs is only Flannel provided by Ksctl

You can only choose CNI plugin during the cluster creation process.
{{% /alert %}}

## Version selection

Default: `latest`

Now you can choose the Flannel version you want to install.

![](/img/cni-flannel-addon-ver.png)
