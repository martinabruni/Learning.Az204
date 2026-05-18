---
title: "Slot Swapping"
type: concept
tags: [deployment-slots, slot-swap, blue-green, zero-downtime, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf,
          learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_4-swap-deployment-slots.pdf]
created: 2025-01-15
updated: 2026-05-15
---

# Slot Swapping

## Definition

**Slot swapping** is the mechanism by which [[azure-app-service]] atomically switches content and routing between two [[deployment-slot|deployment slots]] (e.g. staging → production) without downtime.

## Why It Enables Zero Downtime

App Service warms up all instances of the source slot before switching routing rules. No requests are dropped during the swap.

## Swap Process Summary

1. Apply target slot settings to source slot instances → restart source.
2. Wait for all source instances to restart successfully.
3. (Optional) Initialise local cache on source instances.
4. (Optional) Run custom warm-up via `applicationInitialization`.
5. Switch routing rules — source becomes production.
6. Apply source settings to the former production (now staging) instances.

## Swap Variants

| Variant | Description |
|---------|-------------|
| Standard swap | Immediate — no validation pause |
| Swap with preview | Pause after step 1; validate before completing |
| Auto swap | Triggered automatically on deployment (Windows only) |

## Rollback

After swap, old production resides in the staging slot. Swap again to roll back.

## Settings That Swap vs. Settings That Don't

- **Swapped**: app settings and connection strings (non-sticky), general settings, handler mappings, public certificates, WebJobs content
- **Not swapped**: publishing endpoints, custom domain names, non-public certificates and TLS/SSL settings, scale settings, IP restrictions, WebJobs schedulers, diagnostic settings, CORS settings

## Related Pages

- [[slot-swapping-mechanics]] – step-by-step source page
- [[swap-deployment-slots]] – how-to source page
- [[deployment-slot]] – entity page
- [[application-settings]] – slot-specific vs swapped settings
- [[traffic-routing]] – route traffic without swapping
