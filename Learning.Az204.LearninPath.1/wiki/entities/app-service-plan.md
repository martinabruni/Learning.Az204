---
title: "App Service Plan"
type: entity
tags: [app-service, app-service-plan, pricing, scaling, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_3-azure-app-service-plans.pdf,
          learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# App Service Plan

## What It Is

An **App Service Plan** defines the compute resources (VM type, region, OS, number of instances) on which [[azure-app-service]] apps run. One or more apps can share a single plan.

## Plan Attributes

- Operating System (Windows / Linux)
- Region (e.g. West Europe, East US)
- Number of VM instances
- VM instance size (e.g. P1v3)
- Pricing tier

## Pricing Tiers

| Tier Category | Tiers | Key Characteristics |
|---------------|-------|---------------------|
| Shared compute | Free, Shared | Shared VMs; CPU quotas; no scale-out |
| Dedicated compute | Basic, Standard, Premium, PremiumV2, PremiumV3 | Dedicated VMs; scale-out supported |
| Isolated | Isolated, IsolatedV2 | Dedicated VMs on dedicated VNets; max scale-out |

## Feature Availability by Tier

| Feature | Minimum Tier |
|---------|-------------|
| Autoscale | Standard |
| Deployment slots | Standard |
| App Service Environment | Isolated |
| Always On | Basic |

## Instance Limit for Autoscale

Each plan has an instance limit that autoscale cannot exceed. Higher tiers allow more instances.

## Related Pages

- [[azure-app-service]] – apps running on this plan
- [[autoscale]] – feature of the plan
- [[deployment-slot]] – requires Standard or higher
- [[app-service-environment]] – Isolated tier host environment
- [[examine-app-service-plans]] – source page
