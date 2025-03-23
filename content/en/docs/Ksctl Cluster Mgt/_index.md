---
title: Ksctl Cluster Management
description: Place of all the documentation for the Operators used specifically for k8s clusters
tags: [docs]
---

{{% pageinfo %}}
Ksctl Cluster Management used for ksctl based cluster management.
{{% /pageinfo %}}


## Changelog

### v0.2.0
- added support for `stack` aka ksctl/ka repo

{{% alert color="warning" title="Caution" %}}
Ensure that all resources installed via the addon are completely removed before proceeding with the uninstallation.  

For example, if you have installed the `stack` addon and created a stack named `gitops-standard`, you must delete the `gitops-standard` stack before uninstalling the `stack` addon.
{{% /alert %}}
