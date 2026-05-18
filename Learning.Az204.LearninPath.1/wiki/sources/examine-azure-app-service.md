---
title: "Examine Azure App Service"
type: source
tags: [app-service, overview, containers, ci-cd, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Examine Azure App Service

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf

## Overview

[[azure-app-service]] is a fully managed PaaS platform for web apps, mobile back ends, and RESTful APIs.

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf
> "Azure App Service is a fully managed platform designed to simplify the deployment and scaling of web apps, mobile back ends, and RESTful APIs."

## Supported Runtimes

.NET, Java (SE / Tomcat / JBoss), Node.js, Python, PHP — on Windows or Linux.

## Key Features

### Built-in Auto Scale

Scale up/down (CPU cores, RAM) or scale out/in (instance count). See [[autoscale]].

### Container Support

- Deploy on Windows and Linux.
- Pull from **Azure Container Registry** or **Docker Hub**.
- Supports multi-container apps and **Docker Compose**.

### CI/CD Support

Out-of-the-box integration with Azure DevOps, GitHub, Bitbucket, FTP, and local Git.

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf
> "App Service can automatically sync your code and apply changes as they are pushed to the connected repository."

### Deployment Slots

Use [[deployment-slot|deployment slots]] for blue-green deployments without downtime.

### Compliance

ISO, SOC, and PCI compliant.

## Related Pages

- [[azure-app-service]] – entity page
- [[app-service-plan]] – required compute plan
- [[deployment-slot]] – staging and production slots
- [[autoscale]] – scaling features
- [[container-deployment]] – container-specific features
- [[intro-app-service-introduction]] – module introduction
