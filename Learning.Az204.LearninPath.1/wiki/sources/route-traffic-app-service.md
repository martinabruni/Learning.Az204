---
title: "Route Traffic in App Service"
type: source
tags: [app-service, deployment-slots, traffic-routing, ab-testing, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_5-route-traffic-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Route Traffic in App Service

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_5-route-traffic-app-service.pdf

## Overview

[[traffic-routing]] lets you redirect a percentage of production traffic to a non-production [[deployment-slot|slot]] for A/B testing and beta feedback.

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_5-route-traffic-app-service.pdf
> "By default, all client requests to the app's production URL are routed to the production slot."

## Automatic Traffic Routing

1. Go to app resource page → **Deployment slots**.
2. Set **Traffic %** (0–100) on the target slot.
3. Save.

Specified percentage of clients randomly routed to the non-production slot.

### Session Pinning (Cookie)

| Cookie Value | Slot |
|-------------|------|
| `x-ms-routing-name=staging` | Pinned to staging slot |
| `x-ms-routing-name=self` | Pinned to production slot |

> [!source] learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_5-route-traffic-app-service.pdf
> "After a client is automatically routed to a specific slot, it is 'pinned' to that slot for the life of that client session."

## Manual Traffic Routing

Use the `x-ms-routing-name` query parameter for user opt-in/opt-out:

- Opt **out** of beta: link containing `?x-ms-routing-name=self`
- Opt **into** beta: link containing `?x-ms-routing-name=<slotname>`

## Related Pages

- [[traffic-routing]] – concept page
- [[deployment-slot]] – the slots being routed to
- [[swap-deployment-slots]] – finalize deployment with swap
- [[deployment-slots-introduction]] – module intro
