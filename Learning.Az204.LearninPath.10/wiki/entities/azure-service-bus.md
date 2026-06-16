---
title: "Azure Service Bus"
type: entity
tags: [service-bus, messaging, azure, az204, enterprise-messaging]
sources: [azure-service-bus-overview.md, service-bus-queues-topics-subscriptions.md, service-bus-message-payloads.md, choose-queue-solution.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Service Bus

## What It Is

Azure Service Bus is a **fully managed enterprise message broker** that provides asynchronous message transfer between decoupled applications and services. It supports both **message queues** (point-to-point) and **publish-subscribe topics**.

## Pricing Tiers

| Tier | Use Case | Topics | Transactions | Message Size |
|------|----------|--------|--------------|-------------|
| Basic | Simple low-throughput | No | No | 256 KB |
| Standard | Dev/test, variable load | Yes | Yes | 256 KB |
| Premium | Production, predictable latency | Yes | Yes | Up to 100 MB |

## Core Entities

- **Queue**: FIFO delivery to competing consumers; point-to-point.
- **Topic**: Publish-subscribe; message copies delivered to each subscription.
- **Subscription**: Virtual queue receiving copies of topic messages; supports filter rules.

## Advanced Features

- Message sessions (FIFO with `SessionId`)
- Dead-letter queue (DLQ)
- Autoforwarding
- Scheduled delivery
- Message deferral
- Transactions (within a single messaging entity scope)
- Duplicate detection
- Geo-disaster recovery
- Autodelete on idle (min. 5 minutes)

## Protocols

- Primary: **AMQP 1.0** (ISO/IEC open standard)
- Also: HTTP/REST
- Premium tier: **JMS 2.0** compliant (Java/Jakarta EE)

## Security

- Shared Access Signatures (SAS)
- Role-Based Access Control (RBAC)
- Managed Identities

## When to Choose Service Bus (vs Queue Storage)

See [[choose-queue-solution]] for the full decision guide. Key triggers:
- Need FIFO guarantee
- Need transactions
- Need duplicate detection
- Need topics/pub-sub
- Messages > 64 KB

## Related Pages

- [[azure-service-bus-overview]] – overview source
- [[service-bus-queues-topics-subscriptions]] – queues, topics, subscriptions source
- [[service-bus-message-payloads]] – message structure and serialization source
- [[service-bus-tiers]] – tier comparison concept
- [[service-bus-advanced-features]] – advanced features concept
- [[service-bus-receive-modes]] – peek lock vs receive-and-delete
- [[publish-subscribe-pattern]] – pub/sub pattern concept
- [[amqp]] – AMQP protocol concept
- [[azure-queue-storage]] – alternative queuing service
- [[choose-queue-solution]] – decision guide source
