---
title: "Autoscale"
type: entity
tags: [app-service, autoscale, scaling, performance, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_2-autoscale-factors.pdf,
          learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf,
          learn.microsoft.com_en-us_training_modules_scale-apps-app-service_4-autoscale-app-service.pdf,
          learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Autoscale

## What It Is

**Autoscale** is a feature of [[azure-app-service]] (and its [[app-service-plan]]) that automatically adjusts the number of running VM instances in response to demand or a schedule. It scales **out** (add instances) and **in** (remove instances) — not up/down (instance size).

## Minimum Tier

**Standard** App Service Plan or higher.

## Two Automatic Scaling Modes

| Mode | Description | Min Tier |
|------|-------------|----------|
| Azure Autoscale (rules-based) | You define rules and schedules | Standard |
| Automatic scaling | Platform manages scaling based on HTTP traffic | Premium V2/V3 |

## How Rules Work

1. A **condition** defines when scaling applies (metric or schedule).
2. Each condition contains one or more **rules** that specify:
   - Metric (CPU %, HTTP queue length, etc.)
   - Threshold and operator
   - Time window (duration)
   - Action (add/remove N instances)
3. A **Default condition** runs when no other condition matches.

## Key Best Practices

- Keep meaningful margin between min and max instance counts.
- Use Average statistic for metrics.
- Set different thresholds for scale-out vs. scale-in (avoid flapping).
- Always pair scale-out rules with scale-in rules.
- Monitor via Run History and Activity Log.

## Related Pages

- [[autoscale-conditions-rules]] – conditions and rules concept
- [[autoscale-best-practices]] – best practices concept
- [[app-service-plan]] – plan defines autoscale instance limits
- [[azure-app-service]] – the service being scaled
- [[autoscale-factors]] – comparison with automatic scaling
- [[autoscale-conditions-rules-source]] – source: conditions detail
- [[enable-autoscale-app-service]] – source: enabling autoscale
