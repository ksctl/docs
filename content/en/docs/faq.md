---
title: Faq
description: Frequently asked questions about ksctl
tags: [docs]
---

## General

### What is ksctl?
Ksctl is a lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters. It provides a unified interface for common cluster operations like create, delete, scaleup and down, and is designed to be simple, efficient, and developer-friendly.

### What can I do with ksctl?
With ksctl, you can deploy Kubernetes clusters across any cloud provider, switch between providers seamlessly, and choose between managed and self-managed HA clusters. You can deploy clusters with a single command, without any complex configuration, and manage them with a unified interface that eliminates the need for provider-specific CLIs.

### What are the key features of ksctl?

[Features](features.md)

### How does ksctl simplify cluster management?
Ksctl simplifies cluster management by providing a streamlined interface for common cluster operations like create, delete, scaleup and down. It eliminates the need for complex configuration and provider-specific CLIs, and provides a consistent experience across environments. With ksctl, developers can focus on building great applications without getting bogged down by the complexities of cluster management.

### Who is ksctl for?
Ksctl is designed for developers, DevOps engineers, and anyone who needs to manage Kubernetes clusters. It is ideal for teams of all skill levels, from beginners to experts, and provides a simple, efficient, and developer-friendly way to deploy and manage clusters.

### How does ksctl differ from other cluster management tools?
Ksctl is a lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters. It provides a unified interface for common cluster operations like create, delete, scaleup and down, and is designed to be simple, efficient, and developer-friendly. Ksctl is not a full-fledged platform like Rancher, but rather a simple CLI tool that provides a streamlined interface for common cluster operations.

### How can I get started with ksctl?

[Getting Started](docs/stable/getting-started/)

### How can I contribute to ksctl?


### Where can I find more information about ksctl?

[Documentation](https://docs.ksctl.io)

### How do I update ksctl to the latest version?

### How do I scale a cluster up or down with ksctl?

### How do I switch between cloud providers with ksctl?

### How do I choose between managed and self-managed clusters with ksctl?

### How do I choose between K3s and Kubeadm as the bootstrap provider with ksctl?

### How do I configure storage options with ksctl?

### How do I manage multiple clusters with ksctl?

### How do I provide feedback on ksctl?

### How do I report a bug with ksctl?

[Create Issue](https://github.com/ksctl/ksctl/issues/new/choose)

### How do I request a new feature for ksctl?

[Create Issue](https://github.com/ksctl/ksctl/issues/new/choose)

## Comparisons

Here's an improved and more detailed version based on your recommendations:

## Comparisons

### Ksctl vs Cluster API
- **Simplicity vs Complexity**: Cluster API uses a sophisticated set of CRDs (Custom Resource Definitions) to manage machines, machine sets, and deployments. In contrast, Ksctl adopts a minimalist approach, focusing on reducing complexity for developers and operators.  
- **Target Audience**: Ksctl caters to users seeking a lightweight, user-friendly tool for quick cluster management tasks, particularly in development and testing environments. Cluster API is designed for production-grade use cases, emphasizing flexibility and integration with Kubernetes' declarative model.  
- **Dependencies**: Ksctl is a standalone CLI tool that does not require a running Kubernetes cluster, making it easy to set up and run anywhere. On the other hand, Cluster API requires a pre-existing Kubernetes cluster to operate.  
- **Feature Focus**: Ksctl emphasizes speed and simplicity in managing cluster lifecycle operations (create, delete, scale). Cluster API provides deeper control and automation features suitable for enterprises managing complex Kubernetes ecosystems.


### What is the difference between Ksctl and k3sup?
- **Scope**: Ksctl is a comprehensive tool for managing Kubernetes clusters across multiple environments from cloud managed Kubernetes flavour to K3s and kubeadm. K3sup, on the other hand, focuses primarily on bootstrapping lightweight k3s clusters.  
- **Features**: Ksctl handles infrastructure provisioning, cluster scaling, and cloud-agnostic lifecycle management, whereas k3sup is limited to installing k3s clusters without managing the underlying infrastructure.  
- **Cloud Support**: Ksctl provides a unified interface for managing clusters across different providers, making it suitable for multi-cloud strategies. K3sup is more limited and designed for standalone setups.


### How does Ksctl compare to Rancher?
- **Tool vs Platform**: Ksctl is a streamlined CLI tool for cluster management. Rancher, by contrast, is a feature-rich platform offering cluster governance, monitoring, access control, and application management.  
- **Use Case**: Ksctl is lightweight and ideal for developers needing quick, uncomplicated cluster management. Rancher is tailored for enterprise environments where centralized management and control of multiple clusters are essential.  
- **Operational Scope**: Ksctl focuses on basic lifecycle operations (create, delete, scale). Rancher includes features like Helm chart deployment, RBAC integration, and advanced workload management.


### What is the difference between Ksctl and k3d, Kind, or Minikube?
- **Environment Scope**: Ksctl is designed for both local and cloud-based Kubernetes cluster management. Tools like k3d, Kind, and Minikube are primarily for local development and testing purposes.
- **Cluster Management**: Ksctl can provision, scale, and delete clusters in cloud environments, whereas k3d, Kind, and Minikube focus on providing lightweight clusters for experimentation and local development.
- **Infrastructure Management**: Ksctl integrates with infrastructure provisioning, while the others rely on pre-existing local environments (e.g., Docker for k3d and Kind, or virtual machines for Minikube).


### How does Ksctl compare to eksctl?
- **Cloud Support**: Ksctl is cloud-agnostic and supports multiple providers, making it suitable for multi-cloud setups. Eksctl, on the other hand, is tightly coupled with AWS and designed exclusively for managing EKS clusters.  
- **Features**: Ksctl provides an all-in-one tool for provisioning infrastructure, managing the cluster lifecycle, and scaling across different environments. Eksctl is focused on streamlining EKS setup and optimizing AWS integrations like IAM, VPCs, and Load Balancers.  
- **Target Audience**: Ksctl appeals to users seeking a flexible, multi-cloud solution. Eksctl is ideal for AWS-centric teams that require deep integration with AWS services.


