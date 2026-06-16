---
title: "Service Bus Message Structure"
type: concept
tags: [service-bus, messages, payload, metadata, routing, az204]
sources: [service-bus-message-payloads.md]
created: 2026-06-16
updated: 2026-06-16
---

# Service Bus Message Structure

## Overview

A [[azure-service-bus]] message has two main parts: a **binary payload** and **properties** (broker-defined and user-defined).

## Message Anatomy

| Part | Description |
|------|-------------|
| Binary payload | Opaque binary block; never processed by the broker |
| Broker properties | System-defined; control message-level broker behavior or map to standard metadata |
| User properties | Key-value pairs defined and set by the application |

## Broker Properties for Routing

| Property | Role |
|----------|------|
| `To` | Destination indicator |
| `ReplyTo` | Queue address for replies |
| `ReplyToSessionId` | Session ID for multiplexed reply routing |
| `MessageId` | Unique message identifier |
| `CorrelationId` | Links reply to the original request (copied from `MessageId`) |
| `SessionId` | Groups related messages into a session/stream |

## Routing Patterns

| Pattern | Mechanism |
|---------|-----------|
| Simple request/reply | Sender puts reply queue in `ReplyTo`; consumer echoes `MessageId` into `CorrelationId` of reply |
| Multicast request/reply | Publisher sends to topic; multiple subscribers respond; `ReplyTo` can point to a topic |
| Multiplexing | Session feature routes related messages (by `SessionId`) to a locked receiver |
| Multiplexed request/reply | Publisher sets `ReplyToSessionId`; consumers copy it to `SessionId` of their reply message |

## Payload Serialization

- **ContentType** property: MIME type of the payload (e.g., `application/json;charset=utf-8`).
- **AMQP**: serializes as `ArrayList` / `IDictionary<string,object>`; decodable by any AMQP client; less compatible with HTTP clients.
- **SBMP (legacy)**: uses default binary serializer or external serializer.
- **Best practice**: explicitly serialize object graphs to byte streams before putting them in the payload; reverse on the receiver side.

## Related Pages

- [[azure-service-bus]] – entity page
- [[service-bus-message-payloads]] – source document
- [[amqp]] – AMQP protocol concept
- [[service-bus-queues-topics-subscriptions]] – queues, topics, subscriptions
