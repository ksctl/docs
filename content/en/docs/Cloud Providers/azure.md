---
title: Azure
description: >
  Azure Cloud Provider
categories: [Cloud Provider]
tags: [azure, ha, managed, core]
---

{{% pageinfo %}}
Azure support for HA and Managed Clusters
{{% /pageinfo %}}


{{% alert color="warning" title="Caution" %}}
we need credentials to access clusters

these are confidential information so shouldn't be shared with anyone
{{% /alert %}}


### Azure Subscription ID

subscription id using your subscription

![azure-subscription](/docs/img/azure/azure-subs-id.png)


### Azure Tenant ID

#### Azure Dashboard

Azure Dashboard contains all the credentials required


![azure-dashboard](/docs/img/azure/azure-dashboard.png)

lets get the tenant id from the Azure

![](/docs/img/azure/azure-tenantid.png)



### Azure Client ID

it represents the id of app created


![](/docs/img/azure/azure-app-reg.png)

![](/docs/img/azure/azure-create-app-reg.png)

![](/docs/img/azure/azure-clientid.png)



### Azure Client Secret

it represents the secret associated with the app in order to use it

![create app secret](/docs/img/azure/azure-client-secret1.png)


![after-click](/docs/img/azure/azure-client-secret.png)


![copy-secret](/docs/img/azure/azure-client-secret2.png)

### Assign Role to your app

head over to subscriptions page and click **Access Control (IAM)**
select the **Role Assignment** and then click **Add > Add Role Assignment**
create a new role and when selecting the identity specify the name of the app
Here you can customize the role this app has

![role-assign-app](/docs/img/azure/azure-role-app.png)


## How these credentials are used by ksctl


1. Environment Variables

```bash
export AZURE_TENANT_ID=""
export AZURE_SUBSCRIPTION_ID=""
export AZURE_CLIENT_ID=""
export AZURE_CLIENT_SECRET=""
```

2. Using command line

```bash
ksctl cred
```

## Current Features

### Cluster features
#### Highly Available cluster
clusters which are managed by the user not by cloud provider

    using K3s kubernetes distribution which is lightweight

custom components being used
- MySQL database VM
- HAProxy loadbalancer VM for controlplane nodes
- controlplane VMs
- workerplane VMs

#### Managed Cluster
clusters which are managed by the cloud provider

### Other capabilities

#### Create, Update, Delete, Switch

{{% alert title="Update the cluster infrastructure" %}}

**Managed cluster**: till now it's not supported

**HA cluster**
- addition and deletion of new workerplane node
- SSH access to each cluster node (DB, LB, Controplane, WorkerPlane) _Public Access_, secured by private key

{{% /alert %}}

{{% alert color="success" title="Managed Cluster" %}}

<video width="360" height="202" controls>
<source src="/docs/videos/ksctl-azure-managed.mp4" type="video/mp4" />
Your browser does not support the video tag.
</video>
{{% /alert %}}


{{% alert color="success" title="Highly Available Cluster" %}}

<video width="360" height="202" controls>
<source src="/docs/videos/ksctl-azure-ha.mp4" type="video/mp4" />
Your browser does not support the video tag.
</video>
{{% /alert %}}

