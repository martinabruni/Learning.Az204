---
title: "Explore Staging Environments"
type: source
tags: [app-service, deployment-slots, staging, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_2-app-service-staging-environments.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Explore Staging Environments

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_2-app-service-staging-environments.pdf

## Overview

[[deployment-slot|Deployment slots]] are **live apps** with their own host names that can be swapped with production.

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_2-app-service-staging-environments.pdf
> "Deployment slots are live apps with their own host names. App content and configuration elements can be swapped between two deployment slots, including the production slot."

## Requirements

Available in **Standard, Premium, or Isolated** [[app-service-plan]] tiers only.

## Benefits

| Benefit | Detail |
|---------|--------|
| Validation | Test changes in staging before production swap |
| Zero downtime | Instances are warmed up before swap; traffic is seamless |
| Easy rollback | Old production is in staging slot after swap; swap again to revert |
| Auto swap | Automate for teams without pre-swap validation |

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_2-app-service-staging-environments.pdf
> "The traffic redirection is seamless, and no requests are dropped because of swap operations."

## Slot Limits

Each tier supports a different maximum slot count. Scaling down requires using fewer slots than the target tier supports.

## New Slot Behaviour

A new slot has **no content** even when cloned from another slot's settings.

## Related Pages

- [[deployment-slot]] – entity page
- [[slot-swapping]] – swap mechanics concept
- [[slot-swapping-mechanics]] – detailed swap process
- [[app-service-plan]] – tier requirements
- [[deployment-slots-introduction]] – module intro
