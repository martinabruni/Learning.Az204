---
title: "Swap Deployment Slots"
type: source
tags: [app-service, deployment-slots, slot-swap, auto-swap, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_4-swap-deployment-slots.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Swap Deployment Slots

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_4-swap-deployment-slots.pdf

## Overview

Swapping [[deployment-slot|deployment slots]] enables zero-downtime production releases in [[azure-app-service]].

## Manual Swap

1. Go to **Deployment slots** page → select **Swap**.
2. Select **Source** and **Target** (target = production).
3. Review **Source Changes** and **Target Changes** tabs.
4. Select **Swap** to execute.

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_4-swap-deployment-slots.pdf
> "Before you swap an app from a deployment slot into production, make sure that production is your target slot and that all settings in the source slot are configured exactly as you want to have them in production."

## Swap with Preview (Multi-Phase)

For mission-critical applications — validates with target settings before completing:

1. Check **Perform swap with preview**.
2. Select **Start Swap** — Phase 1 applies target settings to source.
3. Validate staging slot manually.
4. Select **Complete Swap** (or cancel to revert).

## Auto Swap

- **Windows apps only**.
- Configured on the slot; any code push automatically swaps to the target slot.
- Eliminates manual swap step for CI/CD pipelines with automated testing.

## Rollback

After swap, old production resides in the staging slot. **Swap again** to roll back instantly.

## Related Pages

- [[slot-swapping]] – concept overview
- [[slot-swapping-mechanics]] – internal process
- [[deployment-slot]] – entity page
- [[route-traffic-app-service]] – traffic routing between slots
- [[deployment-slots-introduction]] – module intro
