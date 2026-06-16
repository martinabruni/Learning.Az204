---
title: "Azure Kubernetes Service (AKS)"
type: entity
tags: [aks, kubernetes, orchestration, az204]
sources: [aci-overview.md, aca-explore.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Kubernetes Service (AKS)

Azure Kubernetes Service is a **managed Kubernetes service** that simplifies deploying, managing, and scaling containerized applications using Kubernetes.

## Relevance in LP5 Context

- Recommended over [[azure-container-instances]] when full container orchestration is needed: service discovery across multiple containers, automatic scaling, and coordinated application upgrades.
- [[azure-container-apps]] is built **on top of AKS** — ACA abstracts AKS complexity for serverless container scenarios.

## When AKS is Preferred over ACI

- Service discovery across containers
- Automatic scaling of container fleets
- Coordinated application upgrades

## Related Pages

- [[azure-container-instances]] – simpler alternative for isolated workloads
- [[azure-container-apps]] – serverless layer on top of AKS
- [[aci-overview]] – source recommending AKS for orchestration scenarios
