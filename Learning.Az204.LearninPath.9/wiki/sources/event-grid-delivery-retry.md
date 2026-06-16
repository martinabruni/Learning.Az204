---
title: "Explore Event Delivery Durability"
type: source
tags: [event-grid, delivery, retry, dead-letter, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_4-event-grid-delivery-retry.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Event Delivery Durability

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_4-event-grid-delivery-retry.pdf

## Overview

[[azure-event-grid]] provides **durable delivery**: it attempts to deliver each event at least once per matching subscription immediately. On failure, it retries based on a fixed schedule and retry policy.

> "Event Grid doesn't guarantee order for event delivery, so subscribers might receive them out of order."

## Key Claims

- Default delivery: one event at a time (payload is an array with a single event).
- Retry or dead-letter decisions are based on error type from the endpoint.
- Exponential backoff retry policy for transient errors.
- After 30 seconds without a response, message is queued for retry.
- Endpoint responding within 3 minutes: Event Grid attempts to remove from retry queue (duplicates still possible).

## Retry Schedule

Errors that cause **no retry** (event is dead-lettered or dropped):

| Endpoint Type | Error Codes (no retry) |
|--------------|------------------------|
| Azure Resources | 400, 413 |
| Webhook | 400, 413, 401 |

> "If Dead-Letter isn't configured for an endpoint, events are dropped when the above errors happen."

## Retry Policy Configuration

Customizable per event subscription:

| Setting | Range | Default |
|---------|-------|---------|
| Max delivery attempts | 1–30 | 30 |
| Event TTL (minutes) | 1–1440 | 1440 |

Event is dropped if **either** limit is reached.

CLI example:
```bash
az eventgrid event-subscription create \
  -g gridResourceGroup \
  --topic-name <topic_name> \
  --name <event_subscription_name> \
  --endpoint <endpoint_URL> \
  --max-delivery-attempts 18
```

## Output Batching

Off by default; configurable per subscription for high-throughput HTTP scenarios.

| Setting | Description |
|---------|-------------|
| Max events per batch | 1–5,000; actual batch may be smaller if fewer events available |
| Preferred batch size (KB) | Target ceiling; may be exceeded by a single large event |

## Delayed Delivery

When an endpoint experiences repeated failures, Event Grid delays all subsequent retries to that endpoint — up to several hours. Purpose: protect unhealthy endpoints and prevent overwhelming a struggling system.

## Dead-Letter Events

When an event cannot be delivered within TTL or after exhausting attempts, it is sent to a **storage account container** (dead-letter location).

Conditions that trigger dead-lettering:
1. Event not delivered within TTL.
2. Delivery attempt count exceeds the limit.

- Must be enabled explicitly (not on by default).
- 400 or 413 responses immediately schedule dead-lettering.
- 5-minute delay between last delivery attempt and dead-letter write.
- If dead-letter location unavailable for 4 hours → event is dropped.

## Custom Delivery Properties

Up to **10 custom HTTP headers** per event subscription (each value ≤ 4,096 bytes). Supported destinations:
- Webhooks
- Azure Service Bus topics and queues
- Azure Event Hubs
- Relay Hybrid Connections

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-overview]] — core concepts
- [[event-grid-delivery-retry-concept]] — concept page
- [[dead-letter-pattern]] — dead-lettering concept
