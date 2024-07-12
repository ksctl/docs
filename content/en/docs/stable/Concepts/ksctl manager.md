---
title: Core Manager
description: >
  The Component of Ksctl responsible for managing Cloud controller and Distribution controller. It has multiple types of managers
categories: [Examples]
---

{{% pageinfo %}}
It is responsible for managing client requests and calls the corresponding controller
{{% /pageinfo %}}

## Types

### ManagerClusterKsctl
`Role`: Perform ksctl **getCluster**, **switchCluster**

### ManagerClusterKubernetes
`Role`: Perform ksctl **addApplicationAndCrds**
Currently to be used by machine to machine not by ksctl cli

### ManagerClusterManaged
`Role`: Perform ksctl **createCluster**, **deleteCluster**

### ManagerClusterSelfManaged
`Role`: Perform ksctl **createCluster**, **deleteCluster**, **addWorkerNodes**, **delWorkerNodes**
