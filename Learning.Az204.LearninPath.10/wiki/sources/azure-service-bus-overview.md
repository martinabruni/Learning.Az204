---
title: "Explore Azure Service Bus"
type: source
tags: [service-bus, messaging, az204, amqp, tiers]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_3-azure-service-bus-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Service Bus

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_3-azure-service-bus-overview.pdf

## Overview

[[azure-service-bus]] is a **fully managed enterprise message broker** with message queues and publish-subscribe topics. It is used to decouple applications and services by transferring data via messages.

> "A message is a container decorated with metadata, and contains data. The data can be any kind of information, including structured data encoded with the common formats such as the following ones: JSON, XML, Apache Avro, and Plain Text."

## Common Messaging Scenarios

- **Messaging**: Transfer business data (sales orders, journals, inventory movements).
- **Decouple applications**: Improve reliability and scalability; client and service don't need to be online at the same time.
- **Topics and subscriptions**: Enable 1:n relationships between publishers and subscribers.
- **Message sessions**: Implement workflows requiring message ordering or deferral.

## Service Bus Tiers

| Feature | Basic | Standard | Premium |
|---------|-------|----------|---------|
| Throughput | Low | Variable | High |
| Performance | N/A | Variable latency | Predictable |
| Pricing | Pay as you go | Pay as you go variable | Fixed per messaging unit |
| Scaling | N/A | N/A | Scale up and down |
| Message size | 256 KB | 256 KB | Up to 100 MB |
| Topics & Subscriptions | Not supported | Supported | Supported |
| Transactions | Not supported | Supported | Supported |
| Auto-forwarding | Not supported | Supported | Supported |
| Message sessions | Not supported | Supported | Supported |

- **Basic**: Simple scenarios, queues only.
- **Standard**: Dev/test or low-throughput; queues + topics.
- **Premium**: Production; predictable latency, CPU/memory isolation, scales up/down, JMS 2.0 compliant.

## Advanced Features

| Feature | Description |
|---------|-------------|
| Message sessions | FIFO guarantee via exclusive ordered handling of related message sequences |
| Autoforwarding | Chains queue/subscription to another queue or topic in the same namespace |
| Dead-letter queue (DLQ) | Holds messages that cannot be delivered; inspectable and removable |
| Scheduled delivery | Submit messages for delayed processing at a specific time |
| Message deferral | Client defers retrieval; message remains in queue but is set aside |
| Transactions | Groups multiple operations on a single messaging entity in one execution scope |
| Filtering and actions | Subscribers define rules to select messages from a topic |
| Autodelete on idle | Automatically deletes queue after idle interval (minimum 5 minutes) |
| Duplicate detection | Discards duplicate copies if sender resends the same message |
| Security protocols | SAS, RBAC, Managed Identities |
| Geo-disaster recovery | Continues data processing in a different region during downtime |

## Protocols and Compliance

- Primary wire protocol: **AMQP 1.0** (open ISO/IEC standard); compatible with ActiveMQ, RabbitMQ.
- Also supports **HTTP/REST**.
- Service Bus **Premium** is fully compliant with **Java/Jakarta EE JMS 2.0 API**.

## Client Libraries (Azure SDK)

- .NET, Java, Java JMS 2.0, JavaScript/TypeScript, Python.

## Related Pages

- [[azure-service-bus]] – entity page
- [[service-bus-tiers]] – concept: tier comparison
- [[service-bus-advanced-features]] – concept: DLQ, sessions, transactions, etc.
- [[service-bus-queues-topics-subscriptions]] – queues, topics, subscriptions detail
- [[amqp]] – protocol concept
