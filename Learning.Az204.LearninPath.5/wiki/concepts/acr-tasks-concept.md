---
title: "ACR Tasks"
type: concept
tags: [acr, acr-tasks, ci-cd, container-images, automation, az204]
sources: [acr-tasks.md, acr-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# ACR Tasks

ACR Tasks is a cloud-native CI/CD capability built into [[azure-container-registry]]. It automates the container image lifecycle without requiring a local Docker installation.

## Task Types

| Type | Trigger | Description |
|---|---|---|
| Quick task | Manual (`az acr build`) | On-demand build and push; equivalent to `docker build` + `docker push` in the cloud |
| Source code trigger | Git commit / PR | Webhook-based build on code push to GitHub or Azure DevOps |
| Base image trigger | Base image update | Automatically rebuilds dependent images when base image changes |
| Scheduled task | Timer | Cron-like scheduled builds for maintenance or testing |
| Multi-step task | Any trigger | YAML-defined workflow with multiple build, test, push, and deploy steps |

## Multi-Step Task Capabilities

Defined in a YAML file, multi-step tasks can:
- Build images
- Run containers as test environments
- Execute tests against running containers
- Build Helm chart packages
- Execute `helm upgrade`

## Image Platform Support

Default: Linux AMD64. Use `--platform` to target:

| OS | Architectures |
|---|---|
| Linux | AMD64, Arm, Arm64, 386 |
| Windows | AMD64 |

## Inner-Loop Development with Quick Tasks

Quick tasks move image builds to the cloud, enabling developers to verify builds without a local Docker daemon — catching problems before code is committed.

## Related Pages

- [[azure-container-registry]] – entity page
- [[acr-tasks]] – source page
- [[dockerfile-concept]] – related concept
