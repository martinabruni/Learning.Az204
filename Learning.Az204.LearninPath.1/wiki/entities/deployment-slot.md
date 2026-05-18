---
title: "Deployment Slot"
type: entity
tags: [app-service, deployment-slots, staging, blue-green, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_2-app-service-staging-environments.pdf,
          learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf,
          learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_4-swap-deployment-slots.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Deployment Slot

## What It Is

A **deployment slot** is a separate live app environment within [[azure-app-service]] with its own host name. Slots enable staging, testing, and zero-downtime production deployments via [[slot-swapping|slot swaps]].

## Requirements

- **Standard, Premium, or Isolated** [[app-service-plan]] tier.
- No extra charge for using slots.

## Benefits

1. Validate app changes in staging before production.
2. Zero-downtime swap: instances warmed up before routing traffic.
3. Instant rollback: swap again to restore previous version.
4. Auto swap: automatic swap on code push (Windows only).

## Slot-Specific Settings (Not Swapped)

- Custom domain names
- Non-public certificates and TLS/SSL settings
- Publishing endpoints
- Scale settings
- IP restrictions

## Traffic Routing

Use [[traffic-routing]] to send a percentage of production traffic to a non-production slot for A/B testing (see [[route-traffic-app-service]]).

## Session Pinning

Clients routed to a slot are pinned via the `x-ms-routing-name` cookie.

## Related Pages

- [[slot-swapping]] – the swap mechanism
- [[slot-swapping-mechanics]] – step-by-step internal process
- [[swap-deployment-slots]] – how to perform a swap
- [[staging-environments]] – benefits and setup
- [[traffic-routing]] – A/B traffic routing
- [[application-settings]] – slot-specific vs swapped settings
- [[app-service-plan]] – tier requirements
- [[azure-app-service]] – the hosting service
