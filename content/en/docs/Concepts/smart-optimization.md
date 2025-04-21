---
title: Smart Cost & Emission Optimization
description: Documentation on Ksctl's intelligent region and instance selection features
weight: 5
tags: [docs, concepts, optimization]
---

# Smart Cost & Emission Optimization

Ksctl provides intelligent optimization features that help you minimize infrastructure costs and environmental impact when deploying Kubernetes clusters. These features ensure that your clusters run in both the most cost-effective and environmentally friendly configurations.

## Ksctl Optimizer (KO) (v2.4+)

Introduced in **Ksctl v2.4**, KO optimizes costs and emissions by intelligently selecting the most efficient region for your Kubernetes clusters without changing your instance type.

### Key Benefits

- **🚀 Automatic Region Optimization**: Ksctl intelligently identifies and switches to the most cost-effective and environmentally friendly regions.
- **🛠️ Flexible Region Control**: You can opt to keep your cluster in your preferred region if needed.
- **💰 Cost Savings**: Dynamically adapts to pricing changes across regions, reducing your infrastructure expenses.
- **🌱 Eco-Friendly Operations**: Minimizes carbon footprint through smart region selection.

### How It Works

It evaluates regions based on multiple metrics to determine the optimal location for your Kubernetes clusters:

1. **Direct Carbon Intensity** (Lower is better): Measures the carbon emissions from energy production.
2. **LCA Carbon Intensity** (Lower is better): Evaluates the lifecycle carbon emissions of energy sources.
3. **Renewable Power Percentage** (Higher is better): Highlights regions with higher renewable energy usage.
4. **Low CO₂ Power Percentage** (Higher is better): Focuses on regions with a lower share of carbon-intensive power.

![Ksctl v2.4 KO Feature](/img/blogs/ksctl-new-recommendation.png)
*Visualization of dynamic region switching optimization*

## Ksctl Sustainability Metrics (KSM) (v2.5+)

Introduced in **Ksctl v2.5**, this feature enhances the optimization capabilities through a card-based selection interface that helps you choose the best region and instance type for your Kubernetes clusters based on your specific requirements.

### Smart Region Selection

This feature ranks regions based on emission optimization metrics, ensuring that your Kubernetes clusters are not only cost-effective but also environmentally friendly.

#### Key Benefits

- **🌱 Minimizes carbon footprint** by prioritizing regions with lower emissions.
- **🚀 Automatically ranks regions** using advanced emission metrics.

#### How It Works

The Smart Region Selection evaluates and ranks regions based on the same comprehensive emission metrics used in Dynamic Region Switching:

- **Direct Carbon Intensity**
- **LCA Carbon Intensity**
- **Renewable Power Percentage**
- **Low CO₂ Power Percentage**

![Smart Region Selection Interface](/img/blogs/new_selection_region.png)
*Visualization of region selection optimization based on emission metrics*

### Smart Instance Type Selection

This feature helps you choose the most efficient instance type based on both cost and embodied emissions, ensuring that your Kubernetes clusters are optimized for efficiency and sustainability.

#### Key Benefits

- **💰 Cost Optimization**: Adapts to pricing changes across instance types to reduce infrastructure costs.
- **🌱 Sustainability Focus**: Prioritizes instance types with lower embodied emissions, minimizing your carbon footprint.

#### How It Works

The Smart Instance Type Selection evaluates and ranks instance types based on:

- **Cost Efficiency**: Analyzes and compares pricing across different instance types.
- **Embodied Emissions**: Evaluates the environmental impact of manufacturing and deploying each instance type.

![Instance Type Selection Optimization](/img/blogs/new_selection_instance_type.png)
*Visualization of instance type selection optimization based on cost and embodied emissions*

## Using the Optimization Features

These optimization features are integrated with the `ksctl cluster create` command and work automatically when you create a new Kubernetes cluster.

When you run the cluster creation command, Ksctl will:

1. Analyze available regions and instance types
2. Evaluate cost and emission metrics for each option
3. Present optimized recommendations through an intuitive interface
4. Allow you to select the best options for your specific needs

This ensures you get **maximum cost efficiency** and **minimum emissions** while maintaining performance and reliability for all your Kubernetes deployments.

## Upgrading to Access These Features

To access these optimization features, make sure you're using Ksctl v2.4 or above by running:

```shell
ksctl self-update
```

This will ensure you have the latest version with all the optimization capabilities described in this document.
