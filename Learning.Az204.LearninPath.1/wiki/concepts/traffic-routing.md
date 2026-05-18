---
title: "Traffic Routing"
type: concept
tags: [traffic-routing, ab-testing, deployment-slots, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_understand-app-service-deployment-slots_5-route-traffic-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Traffic Routing

## Definition

**Traffic routing** in [[azure-app-service]] allows directing a configurable percentage of production traffic to a non-production [[deployment-slot|deployment slot]], enabling A/B testing or gradual rollouts.

## Automatic Routing

- Configured via the **Traffic %** column in the Deployment slots blade.
- Percentage (0–100) of clients randomly routed to the target slot.
- Once routed, client is **pinned** to that slot for the session via the `x-ms-routing-name` cookie.

## Cookie Values

| Cookie | Slot |
|--------|------|
| `x-ms-routing-name=self` | Production slot |
| `x-ms-routing-name=<slotname>` | Non-production slot |

## Manual Routing

Use the `x-ms-routing-name` query parameter in hyperlinks:
- Opt out of beta: `?x-ms-routing-name=self`
- Opt into beta: `?x-ms-routing-name=staging`

This lets users choose their experience without changing the global traffic split.

## Use Cases

- Canary deployments (e.g. 5% of traffic to new version)
- Beta testing with opt-in/opt-out for users
- Gathering feedback before a full swap

## Related Pages

- [[route-traffic-app-service]] – source page
- [[deployment-slot]] – entity page
- [[slot-swapping]] – finalize release by swapping
- [[swap-deployment-slots]] – swap steps
