---
title: "Explore Azure Container Instances – Overview"
type: source
tags: [aci, container-instances, container-groups, az204]
sources: [learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_2-azure-container-instances-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Container Instances – Overview

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_2-azure-container-instances-overview.pdf

## Overview

[[azure-container-instances]] (ACI) is a solution for isolated-container scenarios including simple applications, task automation, and build jobs.

## Key Claims

- ACI starts containers in Azure **in seconds**, without creating or managing a VM.
- Container groups can be exposed directly to the internet with an IP address and FQDN.
- Provides **hypervisor-level security** — isolation comparable to a VM.
- Supports **custom CPU core and memory** specifications for optimum utilization.
- Supports both **Windows and Linux** containers via the same API.
- For full orchestration (service discovery, auto-scaling, coordinated upgrades), [[azure-kubernetes-service]] (AKS) is recommended instead.

## Container Groups

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_2-azure-container-instances-overview.pdf
> "A container group is a collection of containers that get scheduled on the same host machine."

- The top-level resource in ACI is the **container group**.
- Containers in a group share lifecycle, resources, local network, and storage volumes.
- Analogous to a **pod** in Kubernetes.
- Multi-container groups support **only Linux** containers; Windows supports single-instance only.

## Deployment Methods

| Method | When to use |
|---|---|
| ARM (Resource Manager) template | When deploying additional Azure resources alongside container instances |
| YAML file | When deploying only container instances (more concise) |

## Resource Allocation

- Resources (CPU, memory) are allocated by **summing** the requests of all instances in the group.
- Two instances each requesting 1 CPU → group is allocated 2 CPUs.

## Networking

- Container groups share a **single IP address** and port namespace.
- Port mapping is **not supported** within the group (containers share port namespace).
- Containers within the group can reach each other via `localhost`.

## Supported Volume Types

- Azure file share
- Secret
- Empty directory
- Cloned git repo

## Common Multi-Container Scenarios

- Web app container + content-pull container
- Application container + logging sidecar
- Application container + monitoring sidecar
- Front-end container + back-end container

## Related Pages

- [[azure-container-instances]] – entity page
- [[container-group]] – concept page
- [[aci-restart-policies]] – restart policies source
- [[aci-environment-variables]] – environment variables source
- [[aci-azure-file-share-mount]] – persistent storage source
