---
title: "Networking Features"
type: concept
tags: [networking, vnet, security, inbound, outbound, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Networking Features

## Definition

**Networking features** in [[azure-app-service]] allow control of inbound (traffic to the app) and outbound (traffic from the app) network connections.

## Deployment Types

| Type | Notes |
|------|-------|
| Multitenant | Free–PremiumV3 SKUs; shared network infrastructure |
| [[app-service-environment|ASE]] | Isolated SKU; single-tenant inside your Azure VNet |

## Inbound Features

| Feature | Purpose |
|---------|---------|
| App-assigned address | Dedicated IP for IP-based SSL |
| Access restrictions | IP-based allow/deny rules |
| Service endpoints | Limit to Azure service traffic |
| Private endpoints | Expose app on private VNet IP |

## Outbound Features

| Feature | Purpose |
|---------|---------|
| Hybrid Connections | Connect to on-premises services |
| Gateway-required VNet integration | Route outbound through VNet gateway |
| Virtual network integration | Standard VNet egress |

## Key Principle

Use **inbound features** for inbound traffic control and **outbound features** for outbound traffic control. They can be combined (with some exceptions).

## Related Pages

- [[network-features-app-service]] – source page
- [[azure-app-service]] – the platform
- [[app-service-environment]] – Isolated tier with full VNet integration
- [[authentication-authorization]] – complement to network access control
