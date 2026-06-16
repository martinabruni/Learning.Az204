---
title: "Choose a Message Queue Solution"
type: source
tags: [messaging, service-bus, queue-storage, az204, decision-guide]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_2-choose-queue-solution.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Choose a Message Queue Solution

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_2-choose-queue-solution.pdf

## Overview

[[azure-service-bus]] and [[azure-queue-storage]] are the two Azure queuing technologies. They have overlapping but distinct feature sets. The choice depends on the solution's requirements.

## Key Claims

### Use Service Bus queues when:

- You need to receive messages **without polling** (long-polling TCP-based receive).
- You require **guaranteed FIFO** ordered delivery.
- You need **automatic duplicate detection**.
- You want to process messages as **parallel long-running streams** (identified by `SessionId`).
- You require **transactional behavior and atomicity** when sending or receiving multiple messages.
- Your messages exceed **64 KB** but stay below 256 KB or 1 MB (Service Bus Premium supports up to **100 MB**).
- You need a **role-based access model** with different rights for senders and receivers.

### Use Storage queues when:

- Your application must store **over 80 GB** of messages.
- You need to **track processing progress** per message (supports resume after worker crash).
- You require **server-side logs** of all transactions against the queue.

## Data Points

| Threshold | Service Bus | Storage Queues |
|-----------|-------------|----------------|
| Max message size | Up to 100 MB (Premium) | 64 KB |
| Max queue size | Not size-limited (namespace) | 80 GB+ per queue |
| FIFO guarantee | Yes (with sessions) | No |
| Duplicate detection | Yes | No |
| Transaction support | Yes | No |
| Server-side logging | No | Yes |

## Relevant Quotes

> "Storage queues and Service Bus queues have a slightly different feature set. You can choose either one or both, depending on the needs of your particular solution."

## Related Pages

- [[azure-service-bus]] – Service Bus entity page
- [[azure-queue-storage]] – Queue Storage entity page
- [[service-bus-queues-topics-subscriptions]] – Queues, topics, subscriptions detail
- [[queue-solution-decision]] – Concept: decision framework
