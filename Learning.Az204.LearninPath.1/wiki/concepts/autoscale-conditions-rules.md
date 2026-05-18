---
title: "Autoscale Conditions and Rules"
type: concept
tags: [autoscale, conditions, rules, scaling, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Autoscale Conditions and Rules

## Definition

**Autoscale conditions** define when scaling applies; **autoscale rules** within conditions specify the trigger metric and action to take.

## Condition Types

| Type | Trigger | Example |
|------|---------|---------|
| Metric-based | Resource metric exceeds threshold | CPU % > 70 for 10 minutes |
| Schedule-based | Specific time/date | Every weekday at 08:00 |

Conditions can combine both types (e.g. scale on CPU, but only between 9am–5pm).

## Default Condition

The **Default** condition executes when no other condition is active. It must represent a safe baseline.

## Rule Anatomy

Each metric-based rule defines:

| Attribute | Description |
|-----------|-------------|
| Metric source | App Service Plan, Storage, Service Bus, App Insights |
| Metric name | CPU %, memory %, HTTP queue length, data in/out |
| Time grain statistic | Average, Min, Max, Sum |
| Operator | GreaterThan, LessThan, etc. |
| Threshold | Numeric trigger value |
| Duration | Aggregation window (e.g. 10 minutes) |
| Action | Add/remove/set instance count |
| Cool-down | Wait time after last scaling event |

## Scale-In Rules

Always create a scale-in rule for each scale-out rule. Without it, instances accumulate and are never removed.

## Related Pages

- [[autoscale-conditions-rules-source]] – source page
- [[autoscale]] – entity overview
- [[autoscale-best-practices]] – best practices
- [[app-service-plan]] – plan limits apply
