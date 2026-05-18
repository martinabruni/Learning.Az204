---
title: "Examine Slot Swapping Mechanics"
type: source
tags: [app-service, deployment-slots, slot-swap, warm-up, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Examine Slot Swapping Mechanics

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf

## Overview

During a [[slot-swapping|slot swap]], App Service ensures the **target slot** does not experience downtime.

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf
> "When you swap two slots, App Service completes the following process to ensure that the target slot doesn't experience downtime."

## Swap Steps

1. **Apply target settings to source**: copy slot-specific app settings, connection strings, CI/CD settings, and auth settings to all source instances → triggers restart.
2. **Wait for restart**: if any instance fails, revert all changes and stop.
3. **Local cache init** (if enabled): GET `/` on each source instance; wait for HTTP response (another restart per instance).
4. **Application Initiation** (if auto swap + custom warm-up): GET `/` on each source instance; warmed when any HTTP response returned.
5. **Switch routing rules**: swap the two slots — target now has warmed-up app.
6. **Mirror operation on former target**: apply source-slot settings to the old app now in the source slot.

## Swapped vs. Slot-Specific Settings

**Swapped** (travel with content):
- App settings and connection strings (non-sticky)
- General settings (framework version, platform bits, web sockets, Always On)
- Handler mappings, public certificates, WebJobs content

**Slot-specific (not swapped)**:
- Publishing endpoints, custom domain names
- Non-public certificates and TLS/SSL settings
- Scale settings, IP restrictions, WebJobs schedulers
- Diagnostic settings, CORS settings

## Swap with Preview (Multi-Phase)

App Service pauses after step 1 — validate the source slot with target settings before completing.

## Related Pages

- [[slot-swapping]] – concept page
- [[deployment-slot]] – entity page
- [[swap-deployment-slots]] – manual swap steps
- [[application-settings]] – slot-specific vs swapped settings
- [[deployment-slots-introduction]] – module intro
