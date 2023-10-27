---
title: Feature Install Applications
tags: [kubernetes-client-go, ksctl]
author: Dipankar Das ([@DipankarDas011](https://twitter.com/DipankarDas011))

---

{{% alert title="Note `Experimental`" %}}
Currently Argocd, Prometheus Stack, Cilium ... is supported
{{% /alert %}}


It provides a way to install common applications like argocd, and many more to come

to use this feature
```bash
ksctl create ha-<cloud-provider> ...  --feature-flag application --apps argocd --cni cilium
```

