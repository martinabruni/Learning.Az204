---
title: "App Service Environment (ASE)"
type: entity
tags: [app-service, ase, isolated, vnet, networking, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_6-network-features.pdf,
          learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# App Service Environment (ASE)

## What It Is

The **App Service Environment (ASE)** is a single-tenant deployment of [[azure-app-service]] that runs directly inside an Azure Virtual Network. It corresponds to the **Isolated** and **IsolatedV2** [[app-service-plan]] pricing tiers.

## Key Characteristics

- **Network isolation**: dedicated VNet — full control over inbound/outbound traffic.
- **Compute isolation**: dedicated VMs not shared with other customers.
- **Maximum scale-out**: supports the highest instance counts.
- Suitable for applications with strict compliance, security, or performance requirements.

## When to Use ASE

- Need to comply with strict network security policies.
- Require a private VNet IP for the app (no public endpoint).
- Need maximum scale-out capacity.
- Need full isolation from other App Service customers.

## Contrast with Multitenant

| Aspect | Multitenant App Service | ASE (Isolated) |
|--------|------------------------|----------------|
| Tenancy | Shared | Single (your apps only) |
| Network | Shared scale unit | Your Azure VNet |
| Inbound IP | Shared / App-assigned | VNet private IP |
| Scale-out | Tier-limited | Maximum |
| Cost | Lower | Higher |

## Related Pages

- [[azure-app-service]] – the service
- [[app-service-plan]] – Isolated tier
- [[networking-features]] – network feature overview
- [[network-features-app-service]] – source page
