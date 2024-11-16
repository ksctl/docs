---
title: Faq
description: Frequently asked questions about ksctl
tags: [docs]
---

## General

### What is ksctl?
Ksctl is a lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters. It provides a unified interface for common cluster operations like create, delete, scaleup and down, and is designed to be simple, efficient, and developer-friendly.

### What can I do with ksctl?
With ksctl, you can deploy Kubernetes clusters across any cloud provider, switch between providers seamlessly, and choose between managed and self-managed clusters. You can deploy clusters with a single command, without any complex configuration, and manage them with a unified interface that eliminates the need for provider-specific CLIs.

### What are the key features of ksctl?

[features.md](Features)

### How does ksctl simplify cluster management?
Ksctl simplifies cluster management by providing a streamlined interface for common cluster operations like create, delete, scaleup and down. It eliminates the need for complex configuration and provider-specific CLIs, and provides a consistent experience across environments. With ksctl, developers can focus on building great applications without getting bogged down by the complexities of cluster management.

### Who is ksctl for?
Ksctl is designed for developers, DevOps engineers, and anyone who needs to manage Kubernetes clusters. It is ideal for teams of all skill levels, from beginners to experts, and provides a simple, efficient, and developer-friendly way to deploy and manage clusters.

### How does ksctl differ from other cluster management tools?
Ksctl is a lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters. It provides a unified interface for common cluster operations like create, delete, scaleup and down, and is designed to be simple, efficient, and developer-friendly. Ksctl is not a full-fledged platform like Rancher, but rather a simple CLI tool that provides a streamlined interface for common cluster operations.

### How can I get started with ksctl?

[Getting Started](getting-started)

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

### How do I request a new feature for ksctl?


## Comparisons

### Ksctl vs Cluster API
- Cluster API uses complex CRDs to make use of machine configs, machine sets, and machine deployments. Ksctl uses a simpler approach to manage clusters, with a focus on simplicity and efficiency.
- Ksctl is designed to be a lightweight, easy-to-use tool that simplifies cluster management, while Cluster API is a more complex, feature-rich solution that requires a deeper understanding of Kubernetes concepts.
- Ksctl is just a Simple CLI tool and can be ran on any machine, while Cluster API requires a Kubernetes cluster to be installed and running.
- Cluster API is meant for production use cases, while Ksctl is more focused on development and testing environments where simplicity and speed are key.

### How does ksctl compare to kubectl?
- Ksctl is a higher-level tool that simplifies the process of managing Kubernetes clusters, while kubectl is a lower-level tool that provides direct access to the Kubernetes API.
- Ksctl abstracts away the complexity of cluster management, allowing developers to focus on building applications, while kubectl requires users to have a deep understanding of Kubernetes concepts and resources.
- Ksctl provides a more user-friendly interface for common cluster operations like create, delete, scaleup and down, while kubectl is more flexible and allows for more fine-grained control over Kubernetes resources.

### What is the difference between ksctl and k3sup?
- Ksctl is a more feature-rich tool that provides a complete solution for managing Kubernetes clusters, while k3sup is a lightweight tool that focuses on bootstrapping k3s clusters.
- Ksctl supports multiple cloud providers, both managed and self-managed clusters, and provides a unified interface for all cluster operations not just bootstraping but also provision the infra layer, while k3sup is more limited in scope and is primarily focused on k3s clusters.

### How does ksctl compare to Rancher?
- Ksctl is a lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters, while Rancher is a more complex, feature-rich platform that provides a wide range of tools for managing Kubernetes clusters.
- Ksctl is not a full-fledged platform like Rancher, but rather a simple CLI tool that provides a streamlined interface for common cluster operations like create, delete, scaleup and down.

### What is the difference between ksctl and k3d or kind or minikube?
- Ksctl is a higher-level tool that simplifies the process of managing Kubernetes clusters, while k3d, kind, and minikube are lower-level tools that provide lightweight Kubernetes environments for development and testing.
- Ksctl is used not just in local setup but also in cloud environments, while k3d, kind, and minikube are primarily focused on local development and testing.

### How does ksctl compare to eksctl?
- Ksctl is a more lightweight, easy-to-use tool that simplifies the process of managing Kubernetes clusters, while eksctl is a more complex, feature-rich tool that is specifically designed for managing clusters on AWS EKS.
- Ksctl is cloud-agnostic and supports multiple cloud providers, while eksctl is tightly integrated with AWS services and is optimized for use with EKS clusters.


