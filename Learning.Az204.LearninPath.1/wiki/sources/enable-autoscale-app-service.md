---
title: "Enable Autoscale in App Service"
type: source
tags: [app-service, autoscale, portal, configuration, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_4-autoscale-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Enable Autoscale in App Service

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_4-autoscale-app-service.pdf

## Overview

This unit covers portal steps to enable and configure [[autoscale]] for an [[azure-app-service]] app.

## Steps to Enable

1. Navigate to the **App Service plan** in the Azure portal.
2. Select **Scale out (App Service plan)** in Settings.
3. Select **Rules Based** in the Scale out method.
4. Select **Configure**.
5. Select **Custom autoscale** to reveal condition groups.

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_4-autoscale-app-service.pdf
> "By default, an App Service Plan only implements manual scaling."

## Tier Restrictions

| Tier | Autoscale Support |
|------|------------------|
| F1, D1 | Single instance only |
| B1 | Manual scaling only |
| S1+, P-level | Full autoscale supported |

## Scale Conditions

- **Default** condition: executes when no other condition is active.
- Metric-based conditions: define min/max instance counts.
- Non-default conditions can include a **schedule**.

## Scale Rules

Defined within metric-based conditions — criteria + action (increase/decrease instance count).

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_4-autoscale-app-service.pdf
> "A metric-based scale condition contains one or more scale rules."

## Monitoring Autoscale

- **Run history chart** in the Azure portal.
- Activity Log alerts for email/SMS/webhook notifications.

## Related Pages

- [[autoscale]] – concept page
- [[autoscale-conditions-rules-source]] – conditions and rules
- [[autoscale-best-practices-source]] – best practices
- [[scale-apps-introduction]] – module intro
