---
title: "Autoscale Conditions and Rules"
type: source
tags: [app-service, autoscale, conditions, rules, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Autoscale Conditions and Rules

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf

## Overview

[[autoscale]] in [[azure-app-service]] is configured through **conditions** and **rules** to specify when to scale out and back in.

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf
> "Autoscaling enables you to specify the conditions under which a web app should be scaled out, and back in again."

## Autoscale and App Service Plan

- Autoscaling is a feature of the [[app-service-plan]].
- Each plan has an **instance limit** — autoscale cannot exceed it.
- Higher tiers support higher instance limits.

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf
> "Not all App Service Plan pricing tiers support autoscaling."

## Condition Types

| Type | Description |
|------|-------------|
| Metric-based | Scale when a metric (CPU, HTTP queue, etc.) crosses a threshold |
| Schedule-based | Scale to a specific count at a defined time/date |

Both types can be combined in one condition (e.g., scale on CPU only between 9am–5pm).

The **Default** condition executes when no other condition matches.

## Scale Rules

Each metric-based condition contains one or more rules:

- **Metric source**: App Service Plan, Storage Account, Service Bus queue, Application Insights
- **Metric examples**: CPU %, memory %, disk queue length, HTTP queue length, data in/out
- **Operator**: GreaterThan, LessThan, etc.
- **Threshold**: numeric value to trigger action
- **Duration**: aggregation time window
- **Action**: increase/decrease/set instance count

Always pair scale-out rules with scale-in rules.

## Related Pages

- [[autoscale-conditions-rules]] – concept page
- [[autoscale]] – concept overview
- [[enable-autoscale-app-service]] – enabling autoscale in portal
- [[autoscale-best-practices-source]] – best practices
- [[scale-apps-introduction]] – module intro
