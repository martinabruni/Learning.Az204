---
title: "Deploy to App Service"
type: source
tags: [app-service, deployment, ci-cd, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_4-deploy-code-to-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Deploy to App Service

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_4-deploy-code-to-app-service.pdf

## Overview

[[azure-app-service]] supports **automated** (CI/CD) and **manual** deployment.

## Automated Deployment (CI/CD)

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_4-deploy-code-to-app-service.pdf
> "Automated deployment, or continuous deployment, is a process used to push out new features and bug fixes in a fast and repetitive pattern with minimal effect on end users."

| Source | Description |
|--------|-------------|
| Azure DevOps Services | Build, test, release, deploy pipeline |
| GitHub | Automatic deploy on push to production branch |
| Bitbucket | Supported; less commonly used |

## Manual Deployment

| Method | Description |
|--------|-------------|
| Git | Push to App Service Git remote URL |
| CLI (`az webapp up`) | Package + deploy; can create new app |
| Zip deploy | Send ZIP via `curl` or HTTP |
| FTP/S | Traditional file transfer |

## Best Practice: Use Deployment Slots

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_4-deploy-code-to-app-service.pdf
> "Whenever possible, use deployment slots when deploying a new production build."

Requires **Standard** tier or higher. Enables zero-downtime releases and easy rollback via [[slot-swapping]].

## Related Pages

- [[deployment-slot]] – slots for zero-downtime deployments
- [[slot-swapping]] – swap mechanics
- [[azure-app-service]] – target platform
- [[intro-app-service-introduction]] – module overview
