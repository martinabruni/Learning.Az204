---
title: "Pub/Sub Pattern"
type: concept
tags: [pub-sub, messaging, microservices, dapr, az204]
sources: [aca-dapr.md, aca-explore.md]
created: 2026-06-16
updated: 2026-06-16
---

# Pub/Sub Pattern

The publish/subscribe (pub/sub) pattern is a **messaging pattern** where publishers send messages to a topic and subscribers receive them via an intermediary **message broker** — without direct coupling.

## How Dapr Implements Pub/Sub in ACA

In [[azure-container-apps]] with [[dapr]]:

1. **Publisher app** sends messages to a Dapr component (e.g., Azure Service Bus topic) via the Dapr sidecar.
2. **Subscriber app** receives messages from the broker via its Dapr sidecar.
3. Apps are decoupled — they only communicate through the Dapr pub/sub component.

## Key Properties

- Apps do not need direct knowledge of each other.
- The broker provides **durability** and **delivery guarantees**.
- Dapr handles retries, acknowledgements, and message routing.

## Dapr Pub/Sub Configuration Example (YAML excerpt)

```yaml
dapr:
  enabled: true
  appId: publisher-app
  appPort: 80
  appProtocol: http
```

## Relationship to ACA Environments

Pub/sub between apps in different environments is not possible via Dapr service invocation. Same-environment apps share Dapr components.

## Related Pages

- [[dapr]] – entity page
- [[aca-dapr]] – source page
- [[azure-container-apps]] – entity page
