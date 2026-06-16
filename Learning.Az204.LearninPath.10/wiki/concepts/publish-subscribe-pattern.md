---
title: "Publish-Subscribe Pattern"
type: concept
tags: [messaging, pub-sub, topics, subscriptions, az204, design-pattern]
sources: [service-bus-queues-topics-subscriptions.md, azure-service-bus-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Publish-Subscribe Pattern

## Overview

The publish-subscribe (pub/sub) pattern is a **one-to-many messaging pattern** where a publisher sends a message once and multiple subscribers each receive a copy. It decouples the sender from the receivers.

## How It Works in Azure Service Bus

- The publisher sends messages to a **Topic**.
- Each registered **Subscription** receives an independent copy of each message.
- Consumers receive messages from their subscription — a **virtual queue** — identically to receiving from a regular queue.
- Subscriptions can define **filter rules** (SQL expressions) to receive only matching messages.
- **Filter actions** can modify matching message properties before delivery to the subscription.

## Comparison: Queue vs Topic/Subscription

| Aspect | Queue (point-to-point) | Topic + Subscriptions (pub/sub) |
|--------|------------------------|----------------------------------|
| Consumers | One consumer per message | Each subscription gets a copy |
| Fan-out | No | Yes |
| Filter messages | No | Yes (per subscription) |
| Use case | Task distribution | Event broadcasting |

## Supported Patterns (in Service Bus subscriptions)

Subscriptions support the same messaging patterns as queues:
- Competing consumer
- Temporal decoupling
- Load leveling
- Load balancing

## Availability

Topics and subscriptions are available on **Standard** and **Premium** tiers of [[azure-service-bus]]. Not available on the Basic tier.

## Related Pages

- [[azure-service-bus]] – entity page
- [[service-bus-queues-topics-subscriptions]] – source document
- [[service-bus-advanced-features]] – filtering and actions, autoforwarding
- [[service-bus-tiers]] – tier availability
- [[queue-solution-decision]] – when pub/sub is appropriate
