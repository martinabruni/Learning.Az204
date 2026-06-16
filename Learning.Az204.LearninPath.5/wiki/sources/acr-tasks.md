---
title: "Build and Manage Containers with ACR Tasks"
type: source
tags: [acr, acr-tasks, container-images, ci-cd, az204]
sources: [learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_4-azure-container-registry-tasks.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Build and Manage Containers with ACR Tasks

> [!source] learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_4-azure-container-registry-tasks.pdf

## Overview

**ACR Tasks** is a suite of features in [[azure-container-registry]] that provides cloud-based container image building and CI/CD automation.

## Key Claims

- ACR Tasks supports Linux, Windows, and **ARM architectures**.
- Extends development lifecycle to the cloud with on-demand builds.
- Automates builds triggered by code updates, base image updates, or timers.

## Task Scenarios

| Scenario | Description |
|---|---|
| **Quick task** | On-demand build and push of a single image; equivalent to `docker build` + `docker push` in the cloud |
| **Trigger on source code update** | Builds when code is committed or a PR is made to a Git repo (GitHub or Azure DevOps) |
| **Trigger on base image update** | Automatically rebuilds dependent images when a base image is updated in the registry or Docker Hub |
| **Schedule a task** | Run on a defined schedule via timer triggers |
| **Multi-step task** | YAML-defined workflows with multiple build, test, push, and deploy steps |

## Quick Task Detail

- Uses `az acr build` command.
- Takes a build context, sends to ACR Tasks, and pushes to the registry by default.
- Enables catching build problems before committing code (inner-loop development).

## Trigger on Source Code Update

```bash
az acr task create \
    --registry <registry-name> \
    --name <task-name> \
    --image <image-name>:<tag> \
    --context <git-repo-url> \
    --branch <branch>
```

ACA creates a webhook that triggers image builds on code commits.

## Multi-Step Task Example

A YAML-defined multi-step task can:
1. Build a web application image
2. Run the web application container
3. Build a web application test image
4. Run tests against the running application
5. Build a Helm chart archive package
6. Perform `helm upgrade` with the new chart

## Image Platforms

Default: **Linux OS, amd64 architecture**. Use `--platform` to specify:

| OS | Supported Architectures |
|---|---|
| Linux | AMD64, Arm, Arm64, 386 |
| Windows | AMD64 |

Format: `--platform Linux/arm64/v8`

## Related Pages

- [[azure-container-registry]] – entity page
- [[acr-overview]] – ACR overview source
- [[dockerfile-components]] – Dockerfile source
- [[acr-tasks-concept]] – concept page
