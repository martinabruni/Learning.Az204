---
title: "App Service Networking Features"
type: source
tags: [app-service, networking, vnet, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# App Service Networking Features

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf

## Overview

[[networking-features]] in [[azure-app-service]] control inbound and outbound network traffic for apps.

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf
> "By default, apps hosted in App Service are accessible directly through the internet and can reach internet-hosted endpoints."

## Deployment Types

| Type | SKUs | Notes |
|------|------|-------|
| Multitenant public service | Free → PremiumV3 | Shared scale unit; no direct network connect |
| App Service Environment (ASE) | Isolated | Single-tenant; runs inside your Azure VNet |

## Multitenant Architecture

- **Front ends**: handle HTTP/HTTPS.
- **Workers**: host customer workload.
- Cannot directly connect customer networks to multitenant App Service.

## Inbound Features

| Feature | Purpose |
|---------|---------|
| App-assigned address | IP-based SSL; dedicated inbound IP |
| Access restrictions | IP allow/deny lists |
| Service endpoints | Restrict to Azure service traffic |
| Private endpoints | Expose app on private VNet IP only |

## Outbound Features

| Feature | Purpose |
|---------|---------|
| Hybrid Connections | Access on-premises resources |
| Gateway-required VNet integration | Route outbound through VNet gateway |
| Virtual network integration | Standard VNet egress routing |

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf
> "Use inbound features to solve inbound problems and outbound features to solve outbound problems."

## Related Pages

- [[networking-features]] – concept page
- [[azure-app-service]] – the service
- [[app-service-environment]] – Isolated tier with full VNet integration
- [[intro-app-service-introduction]] – module overview
