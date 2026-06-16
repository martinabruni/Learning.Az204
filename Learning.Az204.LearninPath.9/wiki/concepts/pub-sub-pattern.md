---
title: "Publish/Subscribe Pattern"
type: concept
tags: [messaging, pattern, pub-sub, event-driven, az204]
sources: [event-grid-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Publish/Subscribe Pattern

The **Publish/Subscribe (Pub/Sub)** pattern is a messaging pattern in which **publishers** send messages to a central broker (a topic or channel) without knowing who will receive them, and **subscribers** receive only the messages they have declared interest in.

## Key Properties

- **Decoupling**: publishers and subscribers are not directly connected.
- **Filtering**: subscribers receive only relevant events (by topic, type, or filter).
- **Fan-out**: a single event can be delivered to multiple subscribers.
- **Asynchronous**: publishers do not wait for subscribers to process events.

## Azure Event Grid Implementation

[[azure-event-grid]] is Azure's managed Pub/Sub service:

- Publishers send events to **topics** (system, custom, or partner).
- Subscribers create **event subscriptions** on those topics.
- Event Grid routes events to **event handlers** (webhooks, Azure services).
- Supports push and pull delivery.

## Contrast with Competing Consumers

| Pattern | Characteristic |
|---------|---------------|
| Competing consumers | Multiple consumers compete for the same message; message processed once |
| Pub/Sub / Partitioned consumer | Multiple consumers each get all messages (or a partition); enables parallelism |

See also [[partitioned-consumer-pattern]] for the Event Hubs variant.

## Related Pages

- [[azure-event-grid]] — Azure's Pub/Sub service
- [[azure-event-hubs]] — streaming service with partitioned consumers
- [[partitioned-consumer-pattern]] — parallel processing model
- [[event-driven-architecture]] — broader architectural pattern
