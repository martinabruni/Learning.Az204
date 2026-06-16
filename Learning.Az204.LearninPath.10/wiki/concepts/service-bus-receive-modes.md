---
title: "Service Bus Receive Modes"
type: concept
tags: [service-bus, peek-lock, receive-and-delete, az204, messaging-patterns]
sources: [service-bus-queues-topics-subscriptions.md]
created: 2026-06-16
updated: 2026-06-16
---

# Service Bus Receive Modes

## Overview

[[azure-service-bus]] supports two modes for receiving messages from queues and subscriptions: **Receive and Delete** and **Peek Lock**.

## Receive and Delete

- Service Bus **immediately marks the message as consumed** and returns it to the consumer.
- **One-step** operation.
- If the consumer crashes before processing the message, the message is **permanently lost**.
- Best for: scenarios where the application can tolerate message loss on failure.

## Peek Lock

- **Two-stage** operation providing at-least-once delivery guarantee.

**Stage 1 — Lock:**
- Service Bus finds the next message, **locks it** (invisible to other consumers), and returns it to the application.

**Stage 2 — Complete or Abandon:**
- On success: application signals completion; Service Bus **marks the message as consumed**.
- On failure: application **abandons** the message; Service Bus **unlocks** it for redelivery to any consumer.
- On lock timeout expiry: Service Bus automatically **unlocks** the message for redelivery.

- Best for: applications that **cannot tolerate missing messages** and require reliable processing.

## Comparison

| Aspect | Receive and Delete | Peek Lock |
|--------|-------------------|-----------|
| Stages | 1 | 2 |
| Message loss on crash | Possible | No (redelivered) |
| Complexity | Simple | Higher |
| At-least-once delivery | No | Yes |
| Lock timeout | N/A | Yes (configurable) |

## Interaction with Dead-Letter Queue

If a message repeatedly fails processing (Peek Lock → abandon cycle), Service Bus can move it to the [[service-bus-advanced-features#dead-letter-queue-dlq|Dead-Letter Queue]] after exceeding the max delivery count.

## Related Pages

- [[azure-service-bus]] – entity page
- [[service-bus-queues-topics-subscriptions]] – source document
- [[service-bus-advanced-features]] – advanced features including DLQ
- [[queue-storage-net-operations]] – Queue Storage uses a similar two-step dequeue pattern
