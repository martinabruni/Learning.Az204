---
title: "Discover the Azure Container Registry"
type: source
tags: [acr, container-registry, az204]
sources: [learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_2-azure-container-registry-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover the Azure Container Registry

> [!source] learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_2-azure-container-registry-overview.pdf

## Overview

[[azure-container-registry]] (ACR) is a **managed registry service** based on the open-source Docker Registry 2.0. It stores and manages container images and related artifacts.

## Use Cases

- Pull images for orchestration systems: Kubernetes, DC/OS, Docker Swarm.
- Pull images for Azure services: AKS, App Service, Batch, Service Fabric.
- Developers push images as part of CI/CD workflows (Azure Pipelines, Jenkins).
- Automate image builds triggered by source code commits or base image updates.

## Service Tiers

| Tier | Key Characteristics |
|---|---|
| **Basic** | Cost-optimized for learning; same programmatic capabilities as higher tiers; lower storage and throughput |
| **Standard** | Same capabilities as Basic; higher storage and throughput; satisfies most production scenarios |
| **Premium** | Highest storage and concurrent operations; adds geo-replication, content trust (image tag signing), and private link with private endpoints |

## Supported Images and Artifacts

- Docker container images (Windows and Linux)
- Helm charts
- Images built to the **OCI Image Format Specification**
- Each image in a repository is a **read-only snapshot**.

## Automated Image Builds

Use **ACR Tasks** to:
- Streamline building, testing, pushing, and deploying images.
- Automate OS and framework patching pipeline.
- Build images automatically when team commits to source control.

## Related Pages

- [[azure-container-registry]] – entity page
- [[acr-storage]] – storage capabilities source
- [[acr-tasks]] – ACR Tasks source
- [[dockerfile-components]] – Dockerfile elements source
