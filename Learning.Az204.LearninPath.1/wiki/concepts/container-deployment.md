---
title: "Container Deployment"
type: concept
tags: [containers, docker, app-service, deployment, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf,
          learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_7-exercise-deploy-containerized-app.pdf,
          learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Container Deployment

## Definition

**Container deployment** in [[azure-app-service]] allows deploying Docker containerised applications on both Windows and Linux hosts.

## Registry Sources

- **Azure Container Registry** (ACR)
- **Docker Hub**
- Private registries (via credentials)

## Supported Scenarios

| Scenario | Support |
|----------|---------|
| Single container (Linux) | Yes |
| Single container (Windows) | Yes |
| Multi-container (Docker Compose) | Yes (Linux) |
| Windows containers | Yes |

## CI/CD for Containers

App Service supports automated deployment from ACR and Docker Hub — container images are updated automatically when a new image is pushed.

## Path Mappings for Containers

Containerised apps can mount **Azure Storage** (Blob or File) at a virtual path inside the container (see [[path-mappings]]).

## Exercise

See [[exercise-deploy-containerized-app]] for a hands-on walkthrough.

## Related Pages

- [[examine-azure-app-service]] – source page (container feature overview)
- [[exercise-deploy-containerized-app]] – source page (lab)
- [[path-mappings]] – storage mounts in containers
- [[azure-app-service]] – the platform
