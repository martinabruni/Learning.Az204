---
title: "Azure App Service"
type: entity
tags: [app-service, paas, azure, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_2-azure-app-service.pdf,
          learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf]
created: 2025-01-15
updated: 2026-05-15
---

# Azure App Service

## What It Is

Azure App Service is a **fully managed PaaS** platform for hosting web applications, mobile back ends, and RESTful APIs on Microsoft Azure. It abstracts infrastructure management so developers can focus on code.

## Supported Runtimes

- .NET / .NET Core
- Java (SE, Tomcat, JBoss EAP)
- Node.js
- Python
- PHP
- Custom containers (Windows and Linux)

## Core Features

| Feature | Description |
|---------|-------------|
| Auto Scale | Scale out/in (instances); scale up/down (VM size) is a separate manual action |
| Container support | Docker, Docker Compose, multi-container |
| CI/CD integration | Azure DevOps, GitHub, Bitbucket, FTP, Git |
| Deployment slots | Staging environments for zero-downtime releases |
| Built-in auth | EasyAuth with multiple identity providers |
| Networking | Inbound/outbound traffic control features |
| Compliance | ISO, SOC, PCI compliant |

## Related Pages

- [[app-service-plan]] – compute resources backing the app
- [[deployment-slot]] – staging/production slot environments
- [[autoscale]] – automatic scaling feature
- [[authentication-authorization]] – built-in EasyAuth
- [[networking-features]] – network traffic control
- [[application-settings]] – environment variable configuration
- [[diagnostic-logging]] – monitoring and debugging
- [[security-certificates]] – TLS/SSL certificate management
- [[container-deployment]] – container-specific deployments
- [[app-service-environment]] – Isolated tier deployment

## Source References

- [[examine-azure-app-service]]
- [[examine-app-service-plans]]
- [[intro-app-service-introduction]]
