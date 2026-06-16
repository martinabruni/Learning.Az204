---
title: "Azure Container Instances (ACI)"
type: entity
tags: [aci, azure, containers, serverless, az204]
sources: [aci-overview.md, aci-restart-policies.md, aci-environment-variables.md, aci-azure-file-share-mount.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Container Instances (ACI)

Azure Container Instances is a managed Azure service for running containers **without managing virtual machines or orchestrators**. It is the fastest and simplest way to run a container in Azure.

## Key Attributes

| Attribute | Value |
|---|---|
| Type | Managed container hosting service |
| Startup time | Seconds |
| Networking | Public IP + FQDN per container group |
| Security | Hypervisor-level isolation |
| Billing | Per-second compute |
| OS Support | Windows and Linux |

## When to Use

- Simple applications and task automation
- Build jobs and run-once workloads
- Scenarios that can operate in isolated containers

## When Not to Use

For full container orchestration (service discovery, auto-scaling, coordinated upgrades), use [[azure-kubernetes-service]] (AKS) instead.

## Core Concepts

- [[container-group]]: top-level resource — collection of containers on the same host
- [[restart-policy]]: `Always`, `Never`, `OnFailure`
- [[secure-environment-variables]]: hide sensitive config from properties view
- [[persistent-storage-containers]]: mount Azure Files shares for stateful workloads

## Limitations

- Multi-container groups: **Linux only**
- Azure file share mounts: **Linux only, must run as root, CIFS only**

## Source Pages

- [[aci-overview]] – overview and container groups
- [[aci-restart-policies]] – restart policy options and CLI
- [[aci-environment-variables]] – env vars and secure values
- [[aci-azure-file-share-mount]] – persistent storage via Azure Files
