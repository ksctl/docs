---
title: About K8s Cluster Autoscaling
date: 2024-01-23
description: >
    Our Findings on how does the K8s Cluster Autoscaling works.
---


## Pod Auto-scaler

[https://cloud.google.com/kubernetes-engine/docs/concepts/horizontalpodautoscaler](https://cloud.google.com/kubernetes-engine/docs/concepts/horizontalpodautoscaler)  
[https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale)

## Cluster Auto-Scaler

This blog might help [The Guide To Kubernetes Cluster Autoscaler by Example](https://www.kubecost.com/kubernetes-autoscaling/kubernetes-cluster-autoscaler/) 

* Information from slack channel (*Kubernetes* **\#karpenter**, **\#auto-scaler**)  
* How does **Karpenter** do it?  
  * Karpenter scales using pending pod pressure.  
  * There are two primary controllers for scale up and scale down  
  * Provisioning\_trigger controller, which will create the nodeclaims or initialize a scale request.[https://github.com/kubernetes-sigs/karpenter/blob/main/pkg/controllers/provisioning/controller.go\#L58](https://github.com/kubernetes-sigs/karpenter/blob/main/pkg/controllers/provisioning/controller.go#L58) ,  The provisioning trigger controller watches for pending pods, and in response to those pending pods it checks if it can schedule them on the existing nodes, if not, karpenter will solve scheduling by creating addtional nodeclaims. We have another set of controllers called the node lifecycle controllers that watch for these nodeclaims, and will launch vms for a given nodeclaim.  
  * Disruption Controller, which will tell karpenter to scale down the nodes. For scale down, we poll the cluster every 10 seconds via the disruption controller. [https://github.com/kubernetes-sigs/karpenter/blob/main/pkg/controllers/disruption/controller.go\#L126](https://github.com/kubernetes-sigs/karpenter/blob/main/pkg/controllers/disruption/controller.go#L126)  We will iterate through all of our disruption methods and see if we can initiate some disruption action based on various factors.  
* How **Cluster-auto-scaler** does it?  
  * for scale up, the CAS looks for pending pods. for scale down, it looks for under-utilized nodes (as calculated by resource usage).  
  * Note that resource usage is sum(resource\_requests) / node\_allocatable  
  * It has nothing to do with "real" utilization  
  * Basically CA's job is to make all the pods able to schedule using as few nodes as possible, all it looks at is scheduling  
  * You can use HPA/VPA to update pods based on actual resource usage and that will in turn trigger CA to add/remove nodes  
* Also found a **paper on CO\_2 efficient karpenter**  
  * Andreasen, J. V. (2024). Carbon Efficient Karpenter: Optimizing Kubernetes Cluster Autoscaling for Carbon Efficiency \[Computer software\]. [https://github.com/JacobValdemar/carbon-efficient-karpenter-thesis](https://github.com/JacobValdemar/carbon-efficient-karpenter-thesis) 


