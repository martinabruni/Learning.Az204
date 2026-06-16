---
title: "Discover Service Bus Queues, Topics, and Subscriptions"
type: source
tags: [service-bus, queues, topics, subscriptions, az204, fifo, peek-lock]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_4-queues-topics-subscriptions.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Service Bus Queues, Topics, and Subscriptions

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_4-queues-topics-subscriptions.pdf

## Overview

The core messaging entities of [[azure-service-bus]] are **queues**, **topics and subscriptions**, and **rules/actions**.

## Queues

- Deliver messages in **First In, First Out (FIFO)** order to one or more competing consumers.
- Only **one consumer** receives and processes each message.
- Messages are **stored durably**, so producers and consumers don't need to be online simultaneously.
- Provide **load-leveling**: consuming application handles average load instead of peak load.
- Provide **loose coupling**: producers and consumers are unaware of each other.
- Created via: Azure portal, PowerShell, CLI, or Resource Manager templates.
- Clients: C#, Java, Python, JavaScript.

## Receive Modes

### Receive and Delete

- Service Bus marks the message as consumed immediately and returns it to the consumer.
- Simplest model; suitable when the application can tolerate missing a message on failure.
- Risk: if consumer crashes after receiving but before processing, the message is lost.

### Peek Lock (two-stage)

1. Service Bus **locks** the message and returns it to the application — other consumers cannot receive it.
2. After processing, the application signals completion; Service Bus marks the message as **consumed**.

- If processing fails, the application can **abandon** the message; Service Bus unlocks it for redelivery.
- A **lock timeout** applies: if the lock expires before processing completes, Service Bus unlocks the message automatically.
- Preferred when the application cannot tolerate missing messages.

## Topics and Subscriptions

- Topics provide a **one-to-many (publish/subscribe)** communication pattern, unlike queues (one-to-one).
- Each published message is made available to **every subscription** registered with the topic.
- Consumers receive messages from a **subscription** (virtual queue), not directly from the topic.
- Subscriptions support the same patterns as queues: competing consumer, temporal decoupling, load leveling, load balancing.

## Rules and Actions

- Subscriptions can define **filter expressions** (SQL-based) to select only matching messages from a topic.
- **Filter actions** can modify message properties for matching messages.
- Properties can be system properties (e.g., `Label`) or custom application properties (e.g., `StoreName`).
- Without a SQL filter, any filter action applies to all messages for that subscription.

## Related Pages

- [[azure-service-bus]] – entity page
- [[service-bus-receive-modes]] – concept: peek lock vs receive-and-delete
- [[publish-subscribe-pattern]] – concept: pub/sub messaging pattern
- [[service-bus-advanced-features]] – advanced features including sessions and DLQ
- [[azure-service-bus-overview]] – Service Bus overview source
