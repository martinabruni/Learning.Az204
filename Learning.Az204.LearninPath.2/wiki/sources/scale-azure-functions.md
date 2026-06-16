---
title: "Scale Azure Functions"
type: source
tags: [azure-functions, scaling, hosting, consumption-plan, premium-plan, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_4-scale-azure-functions.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Scale Azure Functions

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_4-scale-azure-functions.pdf

## Overview

Scaling behaviors differ significantly across [[functions-hosting-plans]]. Maximum instances are per-function app (Consumption) or per-plan (Premium/Dedicated).

## Scaling Comparison Table

| Plan | Scale out | Max # instances |
|------|-----------|----------------|
| Consumption plan | Event driven. Automatically scales even during high load. Adds instances based on incoming trigger events. | Windows: 200 / Linux: 100 |
| Flex Consumption plan | Per-function scaling. Event-driven decisions calculated per function — more deterministic scaling. | Limited by total memory usage across all instances in a given region |
| Premium plan | Event driven. Scale out based on number of events. | Windows: 100 / Linux: 20–100 |
| Dedicated plan | Manual/autoscale | 10–30 (up to 100 with ASE) |
| Container Apps | Event driven. Adds more Functions host instances based on trigger events. | 10–300 |

## Key Data Points

- Linux Consumption plan: limit of **500 instances per subscription per hour** during scale-out.
- Linux Premium plan: can scale to 100 instances in some regions.
- Container Apps: max replicas configurable, honored while cores quota is available.
- Dedicated plan limits vary; see App Service plan limits documentation.

## Key Claims

- Flex Consumption is the most deterministic scaling option: decisions are made per individual function rather than per app.
- Consumption plan is the most elastic but has the lowest per-app instance cap (200 Windows / 100 Linux).
- Premium plan provides event-driven scaling with prewarmed workers — no [[cold-start]].
- Dedicated plan is the only plan with manual scaling; use for predictable, long-running workloads.

## Related Pages

- [[azure-functions]] – entity page
- [[functions-hosting-plans]] – concept
- [[cold-start]] – concept
- [[compare-azure-functions-hosting-options]] – previous source
