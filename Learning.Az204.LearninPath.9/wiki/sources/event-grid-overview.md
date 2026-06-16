---
title: "Explore Azure Event Grid"
type: source
tags: [event-grid, pub-sub, messaging, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_2-event-grid-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Event Grid

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_2-event-grid-overview.pdf

## Overview

[[azure-event-grid]] is a highly scalable, fully managed Pub/Sub message distribution service that offers flexible message consumption patterns using HTTP and MQTT protocols. It enables event-driven serverless architectures, IoT data pipelines, and application integration.

> "Azure Event Grid is a highly scalable, fully managed Pub Sub message distribution service that offers flexible message consumption patterns using the Hypertext Transfer Protocol (HTTP) and Message Queuing Telemetry Transport (MQTT) protocols."

## Key Claims

- Supports MQTT v3.1.1 and v5.0 for IoT solutions.
- Supports both **push delivery** (Event Grid sends to subscriber) and **pull delivery** (subscriber polls Event Grid).
- Conforms to **CloudEvents 1.0** specification (HTTP binding with JSON format).
- Maximum event size: **1 MB**. Events over 64 KB are charged in 64-KB increments.

## Core Concepts

### Publishers
An application that sends events to Event Grid. Can be Azure services, custom apps, or **partners** (external organizations via the Partner Events feature).

### Events and CloudEvents
The smallest unit of information describing something that happened. Includes: source, time, unique ID, and event-specific data. Conforms to [[cloudevents-spec|CloudEvents 1.0]].

Example CloudEvents JSON:
```json
{
  "specversion": "1.0",
  "type": "com.yourcompany.order.created",
  "source": "https://yourcompany.com/orders/",
  "subject": "O-28964",
  "id": "A234-1234-1234",
  "time": "2018-04-05T17:31:00Z",
  "datacontenttype": "application/json",
  "data": { "orderId": "O-28964" }
}
```

### Topics
Holds published events. Types:
- **System topics**: built-in Azure service topics (not visible in subscription).
- **Custom topics**: application or third-party topics.
- **Partner topics**: events from external partners via Partner Events feature.

### Event Subscriptions
Tells Event Grid which events to receive. Supports filtering by event type or subject pattern. Can have expiration dates.

### Event Handlers
Where events are sent for processing. Supported handlers include Azure services and custom webhooks. Delivery guaranteed via retries (HTTP webhook: until 200 OK; Storage Queue: until successfully enqueued).

### Security
Uses Azure RBAC. For push delivery with managed identity, the identity must have the appropriate role (e.g., **Event Hubs Data Sender**).

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-schema]] — event schema details
- [[event-grid-delivery-retry]] — delivery and retry mechanics
- [[event-grid-filtering]] — subscription filtering options
- [[cloudevents-spec]] — CloudEvents 1.0 specification concept
- [[pub-sub-pattern]] — publish/subscribe pattern
