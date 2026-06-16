---
title: "Explore Service Bus Message Payloads and Serialization"
type: source
tags: [service-bus, messages, payload, serialization, amqp, az204]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_5-messages-payloads-serialization.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Service Bus Message Payloads and Serialization

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_5-messages-payloads-serialization.pdf

## Overview

Messages in [[azure-service-bus]] carry a **payload** (binary, opaque) and **metadata** (key-value properties). Metadata alone can sometimes be sufficient to convey information.

## Message Structure

A Service Bus message has:

- **Binary payload section**: opaque to the broker; never processed on the service side.
- **Broker properties** (system-defined): control message-level functionality or map to standardized metadata items.
- **User properties** (application-defined): key-value pairs set by the sender.

## Message Routing and Correlation

Key broker properties for routing: `To`, `ReplyTo`, `ReplyToSessionId`, `MessageId`, `CorrelationId`, `SessionId`.

### Routing Patterns

| Pattern | Description |
|---------|-------------|
| Simple request/reply | Publisher sends to queue; reply address in `ReplyTo`; consumer copies `MessageId` to `CorrelationId` in reply |
| Multicast request/reply | Publisher sends to topic; multiple subscribers respond; `ReplyTo` can point to a topic |
| Multiplexing | Session feature routes related messages (by `SessionId`) to a specific receiver holding the session lock |
| Multiplexed request/reply | Publisher sets `ReplyToSessionId`; consumers copy it to `SessionId` of reply; multiple publishers share one reply queue |

## Payload Serialization

- Payload is always an **opaque binary block** in transit and at rest.
- `ContentType` property describes the payload using MIME content-type (e.g., `application/json;charset=utf-8`).
- **.NET Framework** Service Bus API: supports `BrokeredMessage` with arbitrary .NET objects passed to the constructor.
- **Legacy SBMP protocol**: serializes using the default binary serializer or an externally supplied one.
- **AMQP protocol**: serializes objects into AMQP objects; retrievable with `GetBody<T>()`; serialized as `ArrayList` and `IDictionary<string,object>` — decodable by any AMQP client.
- **Recommendation**: take explicit control of serialization; serialize object graphs into streams before including in a message.

> "While this hidden serialization magic is convenient, if applications should take explicit control of object serialization and turn their object graphs into streams before including them into a message, they should do the reverse operation on the receiver side."

> "While AMQP has a powerful binary encoding model, it's tied to the AMQP messaging ecosystem and HTTP clients have trouble decoding such payloads."

## Related Pages

- [[azure-service-bus]] – entity page
- [[amqp]] – AMQP protocol concept
- [[service-bus-message-structure]] – concept: message properties and routing
- [[service-bus-queues-topics-subscriptions]] – queues and topics source
