---
title: Ksctl Agent
description: Documentation on ksctl agent
categories: [Examples, Placeholders]
tags: [docs]
---


{{% pageinfo %}}
It is a ksctl's solution to infrastructure management and also kubernetes management.

Especially inside the kubertes cluster
{{% /pageinfo %}}


It is a GRPC server running as a deployment. and a fleet of controllers will call it to perform certain operations. For instance, application installation via `stack.application.ksctl.com/v1alpha`, etc.

It will be installed on all kubernetes cluster created via ksctl from >= v1.2.0