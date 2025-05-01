---
title: Cluster Summary and Recommendation
description: Documentation on Ksctl's cluster summary and recommendation features
weight: 5
tags: [docs, concepts, optimization]
---

# Cluster Summary and Recommendation

Ksctl provides you a comprehensive summary of your cluster's configuration and provides both:
- debugging information in entire cluster scope
- recommendation in terms of security

{{% alert color= "info" title="Note" %}}
This feature is available in **Ksctl v2.7+**.

Please note this command will work out of the box for any cluster created by ksctl v2.X+

Also Note this Operation is Read heavy make sure you run this command when you are not doing any heavy operations on the cluster.
{{% /alert %}}

## Here is the demo on how it looks

<video src="/img/cluster-summary.mp4" width="auto" height="450" controls></video>

## Why Cluster Summary?

It will give users access to the important details of their cluster with just a single command `$ ksctl cluster summary`
It will help users with the following:
- **Debugging**: It will help users to debug their cluster in a single command. From:
    - **Errors in Pods failing**, 
    - **metrics** from server to know directly what is wrong with the cluster. 
    - **Cluster Events**
    - **Latency**: It gives you report of what is the latency between you and the cluster
- **Recommendation**: It gives remediation of problems it finds in the cluster. We are currently looking for these problems as of now:
    - **PodSecurityPolicy**: It will check if the PodSecurityPolicy is enabled or not. If not, it will give a recommendation to enable it.
    - **NamespaceQuota**: It will check if the NamespaceQuota is enabled or not. If not, it will give a recommendation to enable it.
    - **PodResourceLimits & Requests**: It will check if the PodResourceLimits & Requests are enabled or not. If not, it will give a recommendation to enable it.
    - **NodePort**: It will check if the NodePort is enabled or not. If not, it will give a recommendation to remove them.

## How to use it?

This subcommand got introduced in **Ksctl v2.7**. You can use it by running the following command for any existing cluster:

```bash
$ ksctl cluster summary
```

