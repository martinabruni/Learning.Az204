---
title: "Examine Azure App Service Plans"
type: source
tags: [app-service, app-service-plan, pricing, scaling, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Examine Azure App Service Plans

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf

## Overview

Every [[azure-app-service]] app runs in an [[app-service-plan]] that defines compute resources.

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf
> "In App Service, an app always runs in an App Service plan. An App Service plan defines a set of compute resources for a web app to run."

## Plan Attributes

- Operating System (Windows / Linux)
- Region
- Number of VM instances
- VM instance size (e.g. P1v3, P2v3)
- Pricing tier (Free → IsolatedV2)

## Pricing Tier Categories

| Category | Tiers | Notes |
|----------|-------|-------|
| Shared compute | Free, Shared | Shared VMs; CPU quotas; no scale-out |
| Dedicated compute | Basic, Standard, Premium, PremiumV2, PremiumV3 | Dedicated VMs; higher tier = more scale-out |
| Isolated | Isolated, IsolatedV2 | Dedicated VMs on dedicated VNets; max scale-out |

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf
> "The Isolated and IsolatedV2 tiers run dedicated Azure VMs on dedicated Azure Virtual Networks."

## Scaling Behaviour

- **Free/Shared**: cannot scale out.
- **Other tiers**: app runs on all VM instances; scaling = adding/removing instances.
- Multiple apps can share one plan (share compute).

## When to Use Separate Plans

- App is resource-intensive.
- Requires independent scaling.
- Needs resources in a different region.

## Related Pages

- [[app-service-plan]] – entity page
- [[azure-app-service]] – the service using this plan
- [[autoscale]] – requires Standard or higher
- [[deployment-slot]] – requires Standard or higher
- [[app-service-environment]] – Isolated tier environment
