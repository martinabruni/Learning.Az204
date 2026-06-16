---
title: "Functions Hosting Plans"
type: concept
tags: [azure-functions, hosting, consumption-plan, premium-plan, dedicated-plan, flex-consumption, container-apps, scaling, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-functions_4-scale-azure-functions.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Functions Hosting Plans

## Overview

The hosting plan for a [[function-app]] determines:
- How the function app scales.
- Resources available per instance.
- Support for advanced features (VNet, Linux containers).
- Timeout limits and pricing model.

## Plans Comparison

| Plan | Billing | Scaling | VNet | Container | Max timeout |
|------|---------|---------|------|-----------|-------------|
| Consumption | Pay-per-execution | Automatic event-driven | No | No | 10 min |
| Flex Consumption | Pay-per-execution | Per-function event-driven | Yes | No | Unbounded |
| Premium | Pre-warmed instances billed | Automatic event-driven | Yes | Linux | Unbounded |
| Dedicated | App Service plan rate | Manual / autoscale | Yes | Linux | Unbounded |
| Container Apps | Container hosting rate | Automatic event-driven | Yes | Linux | Unbounded |

## Consumption Plan

- Default plan.
- Instances added/removed dynamically based on incoming events.
- Cheapest for sporadic workloads.
- Max 200 instances (Windows) / 100 instances (Linux).
- 5-minute default timeout, 10-minute maximum.

## Flex Consumption Plan

- Per-function scaling (not per-app) — most deterministic.
- Supports pre-provisioned (always ready) instances to reduce [[cold-start]].
- Virtual networking supported.
- Instance limit: constrained by total memory usage across all instances in a region.

## Premium Plan

- Prewarmed workers — no [[cold-start]] after idle.
- Max 100 instances (Windows) / 20–100 (Linux, region-dependent).
- Grace period: 60 minutes during scale-in.
- Best for: continuous workloads, VNet requirements, more CPU/memory, long-running code.

## Dedicated Plan

- Runs on an existing [[app-service-plan]].
- Manual scaling or autoscale.
- Max 10–30 instances; 100 with [[app-service-environment]] (ASE).
- Requires **Always On** enabled; grace period 10 minutes during platform updates.
- Best for: predictable billing, long-running scenarios where [[durable-functions]] can't be used.

## Container Apps Plan

- Fully managed containerized environment.
- Max 10–300 instances (configurable replicas, subject to cores quota).
- Best for: custom library packaging, cloud native microservices, avoiding Kubernetes overhead.

## HTTP Trigger Hard Limit

Regardless of plan, HTTP-triggered functions have a **230-second** maximum response time (Azure Load Balancer idle timeout). For longer processing, use [[durable-functions]] async pattern or defer work.

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – entity
- [[cold-start]] – concept
- [[durable-functions]] – concept
- [[app-service-plan]] – used by Dedicated plan (from LP1)
- [[app-service-environment]] – used by Dedicated plan at max scale (from LP1)
- [[compare-azure-functions-hosting-options]] – source
- [[scale-azure-functions]] – source
