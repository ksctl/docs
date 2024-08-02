---
title: Amazon Web Services
description: >
  Amazon Web Services
categories: [Cloud Provider]
tags: [aws, ha, managed, core]
---

{{% pageinfo %}}
Aws support for HA and Managed Clusters
{{% /pageinfo %}}


{{% alert color="warning" title="Caution" %}}
we need credentials to access clusters

these are confidential information so shouldn't be shared with anyone
{{% /alert %}}


## How these credentials are used by ksctl

1. Environment Variables

```bash
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
```

2. Using command line

```bash
ksctl cred
```

## Current Features

### Cluster features
#### Highly Available cluster

clusters which are managed by the user not by cloud provider

you can choose between k3s and kubeadm as your bootstrap tool

custom components being used
- Etcd database VM
- HAProxy loadbalancer VM for controlplane nodes
- controlplane VMs
- workerplane VMs

#### Managed Cluster Elastic Kubernetes Service

we provision Roles `ksctl-*` 2 for each cluster:
- `ksctl-<clustername>-wp-role` for the EKS NodePool
- `ksctl-<clustername>-cp-role` for the EKS controlplane

we utilize the iam:AssumeRole to assume the role and create the cluster


##### Policies aka permissions for the user
here is the policy and role which we are using

1. **iam-role-full-access(Custom Policy)**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor6",
            "Effect": "Allow",
            "Action": [
                "iam:CreateInstanceProfile",
                "iam:DeleteInstanceProfile",
                "iam:GetRole",
                "iam:GetInstanceProfile",
                "iam:RemoveRoleFromInstanceProfile",
                "iam:CreateRole",
                "iam:DeleteRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "iam:ListInstanceProfiles",
                "iam:AddRoleToInstanceProfile",
                "iam:ListInstanceProfilesForRole",
                "iam:PassRole",
                "iam:CreateServiceLinkedRole",
                "iam:DetachRolePolicy",
                "iam:DeleteRolePolicy",
                "iam:DeleteServiceLinkedRole",
                "iam:GetRolePolicy",
                "iam:SetSecurityTokenServicePreferences"
            ],
            "Resource": [
                "arn:aws:iam::*:role/ksctl-*",
                "arn:aws:iam::*:instance-profile/*"
            ]
        }
    ]
}
```

2. **eks-full-access(Custom Policy)**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "eks:ListNodegroups",
                "eks:ListClusters",
                "eks:*"
            ],
            "Resource": "*"
        }
    ]
}
```

3. **AmazonEC2FullAccess(Aws)**
4. **IAMReadOnlyAccess(Aws)**

{{% alert color="info" title="Validaty of Kubeconfig" %}}
The Kubeconfig generated after you ran

```shell
ksctl switch aws --name here-you-go --region us-east-1
```

we are using sst token to authenticate with the cluster, so the kubeconfig is valid for 15 minutes

once you see that there is a error of unauthorized then you need to re-run the above command

{{% /alert %}}
