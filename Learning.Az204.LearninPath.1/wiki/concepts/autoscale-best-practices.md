---
title: "Autoscale Best Practices"
type: concept
tags: [autoscale, best-practices, scaling, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_scale-apps-app-service_5-autoscale-best-practices.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Autoscale Best Practices

## Overview

Following best practices for [[autoscale]] prevents oscillation, runaway scaling, and unexpected costs.

## Best Practices Summary

| Practice | Reason |
|----------|--------|
| Keep margin between min and max | If equal, no scaling action can occur |
| Use Average statistic | Most representative for web workloads |
| Different thresholds for scale-out and scale-in | Prevents flapping/oscillation |
| Always pair scale-out with scale-in | Prevents runaway instance growth |
| Use Default condition as safety net | Ensures baseline capacity when no other condition applies |
| Enable Activity Log notifications | Track and audit all scaling events |

## Threshold Guidance

Anti-pattern (causes flapping):
- Scale out: CPU > 80%
- Scale in: CPU > 60%

Recommended:
- Scale out: CPU > 80%
- Scale in: CPU < 60% ← lower threshold, meaningful gap

## Monitoring

All autoscale events (success and failure) are logged in the **Activity Log**. Set up alerts for email, SMS, or webhooks.

## Related Pages

- [[autoscale-best-practices-source]] – source page
- [[autoscale]] – autoscale entity
- [[autoscale-conditions-rules]] – conditions and rules
- [[enable-autoscale-app-service]] – enabling autoscale
