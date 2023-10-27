---
title: Feature Auto Scaling
tags: [kubernetes-client-go, ksctl]
author: Dipankar Das ([@DipankarDas011](https://twitter.com/DipankarDas011))
---

{{% alert title="Note `Experimental`" %}}
Currently planned to support auto-scaling for self-managed clusters

(Controllers part is under development)
{{% /alert %}}


During creation of the cluster it installs necessary configurations and statefile to the cluster
and also creates a slim version of ksctl core api (aka scaleup and scaledown)

Added then the controller will use certain metrics from metrics server to determine when to call HTTP requests to the ksctl to scaleup or scaledown

to use this feature
```bash
ksctl create ha-<cloud-provider> ...  --feature-flag autoscale
```

### Here is deatiled view

![Propsal design](/ksctl-docs/img/ksctl-auto-scaling-fp.excalidraw.svg)
