---
title: "Service Bus Advanced Features"
type: concept
tags: [service-bus, dlq, sessions, transactions, autoforwarding, az204]
sources: [azure-service-bus-overview.md, service-bus-queues-topics-subscriptions.md]
created: 2026-06-16
updated: 2026-06-16
---

# Service Bus Advanced Features

## Overview

[[azure-service-bus]] includes advanced features beyond basic queuing to address complex enterprise messaging scenarios.

## Feature Reference

### Message Sessions
- Enable **FIFO guarantee** via exclusive, ordered handling of related message sequences.
- Messages are grouped using the `SessionId` property.
- A receiver acquires a session lock and processes all messages in that session.
- Standard and Premium tiers only.

### Autoforwarding
- Chains a queue or subscription to **another queue or topic** within the same namespace.
- Enables fan-out and chained processing pipelines.

### Dead-Letter Queue (DLQ)
- Holds messages that **cannot be delivered** to any receiver.
- Messages can be removed from the DLQ and inspected for debugging.
- Each queue and subscription has its own DLQ.

### Scheduled Delivery
- Submit messages to a queue or topic for **delayed processing** at a specific future time.

### Message Deferral
- A consumer can **defer retrieval** of a specific message to a later time.
- The deferred message remains in the queue but is set aside (not redelivered normally).

### Transactions
- Groups **two or more operations** within a single **execution scope** against a single messaging entity.
- Scope: a queue, topic, or subscription — not cross-entity in a single transaction.
- Guarantees atomicity.

### Filtering and Actions (Topics)
- Subscriptions define **SQL filter expressions** to select matching messages from a topic.
- **Filter actions** can modify message properties for matched messages.
- Properties can be system properties (e.g., `Label`) or custom application properties (e.g., `StoreName`).

### Autodelete on Idle
- Automatically deletes a queue after a configurable idle interval.
- Minimum duration: **5 minutes**.

### Duplicate Detection
- If a sender resends the same message (e.g., due to network uncertainty), Service Bus **discards duplicates**.
- Relies on `MessageId` matching within a detection window.

### Geo-Disaster Recovery
- Continues data processing in a **different Azure region or datacenter** during regional outages.

### Security
- **SAS** (Shared Access Signatures)
- **RBAC** (Role-Based Access Control)
- **Managed Identities**
- Protocols: AMQP 1.0, HTTP/REST

## Related Pages

- [[azure-service-bus]] – entity page
- [[azure-service-bus-overview]] – source document
- [[service-bus-tiers]] – which tier supports which feature
- [[publish-subscribe-pattern]] – pub/sub with filtering
- [[service-bus-receive-modes]] – peek lock and DLQ interaction
