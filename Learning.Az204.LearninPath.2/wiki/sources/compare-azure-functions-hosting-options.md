---
title: "Compare Azure Functions Hosting Options"
type: source
tags: [azure-functions, hosting, consumption-plan, premium-plan, dedicated-plan, flex-consumption, container-apps, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Compare Azure Functions Hosting Options

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf

## Overview

When creating a function app in Azure, you must choose a hosting plan. The hosting option determines scaling behavior, available resources, advanced functionality support, and Linux container support.

## Hosting Plans Summary

| Hosting option | Service | Availability | Container support |
|----------------|---------|--------------|-------------------|
| Consumption plan | Azure Functions | GA | None |
| Flex Consumption plan | Azure Functions | GA | None |
| Premium plan | Azure Functions | GA | Linux |
| Dedicated plan | Azure Functions | GA | Linux |
| Container Apps | Azure Container Apps | GA | Linux |

## Plan Details

### Consumption Plan (default)

- **Pay-as-you-go**: pay for compute only when functions run.
- Instances dynamically added/removed based on incoming events.
- Default hosting plan.

### Flex Consumption Plan

- High scalability with per-function scaling (more deterministic).
- Virtual networking support; pay-as-you-go billing.
- Reduce [[cold-start]] by specifying pre-provisioned (always ready) instances.

### Premium Plan

Use when:
- Function apps run continuously or nearly continuously.
- Need more control over instances; multiple function apps on same plan.
- High number of small executions with high execution bill but low GB-seconds.
- Need more CPU/memory than Consumption plan offers.
- Code needs to run longer than Consumption plan's max execution time.
- Require virtual network connectivity.
- Want a custom Linux image.

### Dedicated Plan

- Runs inside an App Service plan at regular [[app-service-plan]] rates.
- Best for long-running scenarios where [[durable-functions]] can't be used.
- Use when predictable billing is required or manual instance scaling is needed.
- Can use [[app-service-environment]] (ASE) for full compute isolation and high memory/scale.

### Container Apps

- Fully managed environment hosted by Azure Container Apps.
- Use the Azure Functions programming model for event-driven, cloud native functions.
- Run functions alongside microservices, APIs, websites, and workflows.
- Use when: packaging custom libraries, migrating on-premises apps, avoiding Kubernetes complexity, needing dedicated CPU compute.

## Function App Time-out Duration

The `functionTimeout` property in `host.json` controls execution time-out. HTTP triggered functions are always capped at **230 seconds** (Azure Load Balancer idle timeout), regardless of `functionTimeout`.

| Plan | Default (min) | Maximum |
|------|--------------|---------|
| Flex Consumption | 30 | Unbounded |
| Premium | 30 | Unbounded |
| Dedicated | 30 | Unbounded |
| Container Apps | 30 | Unbounded |
| Consumption | 5 | 10 |

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf
> "Regardless of the function app time-out setting, 230 seconds is the maximum amount of time that an HTTP triggered function can take to respond to a request. This is because of the default idle time-out of Azure Load Balancer."

## Key Claims

- Consumption plan is the default and cheapest but has a 10-minute max execution time.
- Premium plan has prewarmed workers — no cold start delay after idle.
- Dedicated plan requires Always On to be set; otherwise apps unload after inactivity.
- Container Apps supports up to 10–300 instances with configurable max replicas.

## Related Pages

- [[azure-functions]] – entity page
- [[functions-hosting-plans]] – concept
- [[cold-start]] – concept
- [[scale-azure-functions]] – next source
- [[app-service-plan]] – Dedicated plan context
- [[app-service-environment]] – Isolated/ASE context
