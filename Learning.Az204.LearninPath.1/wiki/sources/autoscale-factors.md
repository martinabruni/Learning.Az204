---
title: "Examine Scale Out Options"
type: source
tags: [app-service, autoscale, scaling, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_2-autoscale-factors.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Examine Scale Out Options

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_2-autoscale-factors.pdf

## Overview

[[azure-app-service]] offers manual scaling and two automatic scale-out options: rules-based **Autoscale** and platform-managed **Automatic scaling**.

## Comparison Table

| Factor | Autoscale | Automatic Scaling |
|--------|-----------|------------------|
| Available tiers | Standard and up | Premium V2 (P1V2–P3V2), Premium V3 (P0V3–P5MV3) |
| Rule-based scaling | Yes | No |
| Schedule-based scaling | Yes | No |
| Always ready instances | No | Yes (min 1) |
| Prewarmed instances | No | Yes (default 1) |
| Per-app maximum | No | Yes |

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_2-autoscale-factors.pdf
> "Autoscaling is a cloud system or process that adjusts available resources based on the current demand."

## What Triggers Autoscaling?

- CPU utilisation grows
- Memory occupancy increases
- HTTP request surge
- Custom metric combinations
- Time-based schedule

## Key Distinction

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_2-autoscale-factors.pdf
> "Autoscaling performs scaling in and out, as opposed to scaling up and down."

Autoscaling **does not change instance size** (scale up/down); it adds or removes instances.

## Related Pages

- [[autoscale]] – concept page
- [[autoscale-conditions-rules-source]] – conditions and rules
- [[app-service-plan]] – tier determines autoscale availability
- [[scale-apps-introduction]] – module intro
