---
title: "Cold Start"
type: concept
tags: [azure-functions, cold-start, serverless, performance, hosting, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Cold Start

## Definition

A **cold start** occurs when a serverless function is invoked after being idle and the host instance is not already running. The delay is caused by the time needed to provision and initialize a new function host instance before execution can begin.

## Occurrence by Plan

| Plan | Cold start risk |
|------|----------------|
| Consumption | High — instances torn down after idle |
| Flex Consumption | Reduced — can specify always-ready (pre-provisioned) instances |
| Premium | Eliminated — uses prewarmed workers running continuously |
| Dedicated | Eliminated — requires Always On setting |
| Container Apps | Possible when minimum replicas is zero |

## Mitigation Strategies

1. **Premium plan**: uses prewarmed workers that run applications with no delay after being idle.
2. **Flex Consumption plan**: specify the number of pre-provisioned (always ready) instances.
3. **Dedicated plan with Always On**: keeps the app loaded at all times.

## Impact

Cold starts increase latency for the first request after an idle period. For latency-sensitive applications, the Premium plan or Flex Consumption with pre-provisioned instances is recommended over the basic Consumption plan.

## Related Pages

- [[functions-hosting-plans]] – which plans mitigate cold starts
- [[azure-functions]] – entity
- [[compare-azure-functions-hosting-options]] – source
- [[scale-azure-functions]] – source
