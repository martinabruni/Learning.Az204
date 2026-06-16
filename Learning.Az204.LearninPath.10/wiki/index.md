---
title: "Wiki Index – AZ-204 Learning Path 10: Azure Message Queues"
type: synthesis
tags: [index, az204, service-bus, queue-storage, messaging]
sources: [choose-queue-solution.md, azure-service-bus-overview.md, service-bus-queues-topics-subscriptions.md, service-bus-message-payloads.md, azure-queue-storage-overview.md, queue-storage-dotnet.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 10: Azure Message Queues

This wiki is built from 6 PDFs in `raw/`, all from the Microsoft Learn module `discover-azure-message-queue`.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-service-bus]] | Fully managed enterprise message broker with queues and pub/sub topics |
| [[azure-queue-storage]] | Azure Storage service for large-scale asynchronous message backlogs |
| [[azure-storage-account]] | Gateway to all Azure Storage services; hosts Queue Storage queues |

---

## Concepts

| Page | Summary |
|------|---------|
| [[queue-solution-decision]] | Decision framework: when to use Service Bus vs Queue Storage |
| [[service-bus-tiers]] | Basic, Standard, Premium tier comparison for Service Bus |
| [[service-bus-advanced-features]] | DLQ, sessions, transactions, deduplication, autoforwarding, geo-DR |
| [[service-bus-receive-modes]] | Receive-and-delete vs peek-lock; at-least-once delivery pattern |
| [[publish-subscribe-pattern]] | 1:n pub/sub via Service Bus topics and subscriptions |
| [[service-bus-message-structure]] | Message anatomy: payload, broker properties, user properties, routing patterns |
| [[amqp]] | AMQP 1.0 open protocol used by Service Bus; interoperability with ActiveMQ/RabbitMQ |
| [[queue-storage-net-operations]] | .NET SDK patterns for Queue Storage: two-step dequeue, peek, update, delete |

---

## Sources

| Page | PDF (unit) |
|------|-----------|
| [[choose-queue-solution]] | `_2-choose-queue-solution.pdf` |
| [[azure-service-bus-overview]] | `_3-azure-service-bus-overview.pdf` |
| [[service-bus-queues-topics-subscriptions]] | `_4-queues-topics-subscriptions.pdf` |
| [[service-bus-message-payloads]] | `_5-messages-payloads-serialization.pdf` |
| [[azure-queue-storage-overview]] | `_7-azure-queue-storage-overview.pdf` |
| [[queue-storage-dotnet]] | `_8-queue-storage-code-examples.pdf` |

---

## Page Counts

- Sources: 6
- Entities: 3
- Concepts: 8
- **Total wiki pages: 17** (plus this index and log.md)
