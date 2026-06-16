---
title: "AMQP (Advanced Message Queuing Protocol)"
type: concept
tags: [amqp, messaging, protocol, service-bus, az204]
sources: [azure-service-bus-overview.md, service-bus-message-payloads.md]
created: 2026-06-16
updated: 2026-06-16
---

# AMQP (Advanced Message Queuing Protocol)

## Overview

AMQP 1.0 is the **primary wire protocol** for [[azure-service-bus]]. It is an open ISO/IEC standard for message-oriented middleware.

## Key Characteristics

- **Open standard**: ISO/IEC standardized; interoperable with on-premises brokers such as ActiveMQ and RabbitMQ.
- **Binary encoding**: Powerful, compact binary format; serializes objects as `ArrayList` and `IDictionary<string,object>`.
- **TCP-based**: Enables long-polling; consumers can receive messages without active polling loops.
- **Decodable**: Any AMQP client can decode the serialized object graph.
- **HTTP client limitation**: AMQP's binary encoding is **not easily decoded by HTTP clients** — prefer explicit serialization (e.g., JSON) for cross-protocol compatibility.

## Usage in Service Bus

- All Service Bus tiers use AMQP 1.0.
- Service Bus Premium tier is also JMS 2.0 compliant (Java/Jakarta EE).
- The Azure SDK client libraries for .NET, Java, JavaScript/TypeScript, and Python all use AMQP under the hood.

## Compatibility

- Works with on-premises AMQP brokers: ActiveMQ, RabbitMQ.
- Customers can write applications that work against both Service Bus and on-premises brokers.

## Related Pages

- [[azure-service-bus]] – primary user of AMQP
- [[azure-service-bus-overview]] – source document
- [[service-bus-message-structure]] – message serialization using AMQP
- [[service-bus-message-payloads]] – source document on serialization
