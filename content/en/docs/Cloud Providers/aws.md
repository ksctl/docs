---
title: Amazon Web Services
description: >
  Amazon Web Services
categories: [Cloud Provider]
tags: [aws, ha, managed, core]
---

{{% pageinfo %}}
AWS integration for High Availability and Managed Kubernetes Clusters
{{% /pageinfo %}}

{{% alert color="warning" title="Caution" %}}
AWS credentials are required to access clusters. These credentials are sensitive information and must be kept secure.
{{% /alert %}}

## Authentication Methods

### Environment Variables
Set the following environment variables:
```bash
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
```

### Command Line Interface
Use the ksctl credential manager:
```bash
ksctl cred
```

## Available Cluster Types

### Highly Available (HA) Clusters
Self-managed clusters with the following components:
- Distributed etcd database instances
- HAProxy load balancer for control plane high availability
- Multiple control plane nodes
- Worker nodes

Choose between two bootstrap options:
- k3s (lightweight Kubernetes distribution)
- kubeadm (official Kubernetes bootstrap tool)

### Amazon EKS (Managed Clusters)
Elastic Kubernetes Service deployment with automated:
- IAM role creation and management
- Control plane setup
- Node group configuration

#### IAM Configuration
For each cluster, ksctl creates two roles:
- `ksctl-<clustername>-wp-role`: Manages node pool permissions
- `ksctl-<clustername>-cp-role`: Handles control plane access

#### Required IAM Policies

1. **Custom IAM Role Access Policy**
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

2. **Custom EKS Access Policy**
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

3. **AWS Managed Policies Required**
- AmazonEC2FullAccess
- IAMReadOnlyAccess

{{% alert color="info" title="Kubeconfig Authentication" %}}
After switching to an AWS cluster using:
```shell
ksctl switch aws --name here-you-go --region us-east-1
```
The generated kubeconfig uses AWS STS tokens which expire after 15 minutes. When you encounter authentication errors, simply run the switch command again to refresh the credentials.
{{% /alert %}}


## Looking for CLI Commands?

All CLI commands mentioned in this documentation have detailed explanations in our command reference guide.

{{% alert title="CLI Reference" %}}
👉 Check out our comprehensive [CLI Commands Reference](/docs/develop/reference/) for:
- Detailed command syntax
- Usage examples
- Available options and flags
- Common use cases
{{% /alert %}}
