---
title: "Autoscale Best Practices"
type: source
tags: [app-service, autoscale, best-practices, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Autoscale Best Practices

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf

## Overview

Poorly configured [[autoscale]] rules can cause oscillation or runaway scaling. This unit covers best practices.

## Core Concepts

- Scales **horizontally**: out (more instances) and in (fewer instances).
- Has maximum, minimum, and default instance counts.
- Thresholds are **calculated at instance level** (average across all instances).
- All events logged to the **Activity Log**.

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf
> "All autoscale successes and failures are logged to the Activity Log."

## Best Practices

### 1. Adequate Margin Between Min and Max
If min == max == current count, no scaling can occur. Keep a meaningful gap.

### 2. Choose the Right Metric Statistic
Options: Average, Minimum, Maximum, Total. **Average** is most appropriate for most workloads.

### 3. Careful Threshold Selection
Use **different thresholds** for scale-out and scale-in to prevent flapping (oscillation):
- Bad: scale-out at CPU > 80%, scale-in at CPU > 60% (endless toggling)
- Good: scale-out at CPU > 80%, scale-in at CPU < 60%

> [!source] learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf
> "We recommend carefully choosing different thresholds for scale-out and scale-in based on practical situations."

### 4. Always Pair Scale-Out with Scale-In
Prevents runaway instance growth.

### 5. Use Notifications
Configure Activity Log alerts (email, SMS, webhook) to track autoscale events.

### 6. Default Condition Safety
The Default condition must represent a safe baseline instance count.

## Related Pages

- [[autoscale-best-practices]] – concept page
- [[autoscale-conditions-rules-source]] – conditions and rules
- [[enable-autoscale-app-service]] – enabling autoscale
- [[autoscale]] – concept overview
