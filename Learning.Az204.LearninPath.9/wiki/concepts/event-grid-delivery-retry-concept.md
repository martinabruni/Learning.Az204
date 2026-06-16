---
title: "Event Grid Delivery and Retry"
type: concept
tags: [event-grid, delivery, retry, dead-letter, durability, az204]
sources: [event-grid-delivery-retry.md]
created: 2026-06-16
updated: 2026-06-16
---

# Event Grid Delivery and Retry

[[azure-event-grid]] provides **durable event delivery** with a configurable retry policy, dead-lettering, and output batching.

## Delivery Guarantees

- **At-least-once delivery**: Event Grid attempts to deliver each event at least once per subscription.
- **No ordering guarantee**: subscribers may receive events out of order.

## Retry Behavior

- Exponential backoff with small randomization.
- Events may be skipped on specific retries if endpoint is consistently unhealthy.
- 30-second wait for a response before queuing for retry.
- If endpoint responds within 3 minutes: Event Grid tries to remove from retry queue (duplicates may still occur).

### Errors That Skip Retry

| Endpoint | Codes |
|----------|-------|
| Azure Resources | 400, 413 |
| Webhook | 400, 413, 401 |

## Retry Policy Parameters

| Setting | Range | Default |
|---------|-------|---------|
| Max delivery attempts | 1–30 | 30 |
| Event TTL | 1–1440 min | 1440 min |

## Dead-Letter Events

When delivery fails permanently (TTL exceeded or max attempts reached), the event is sent to a **dead-letter storage container** (if configured). 

- Not enabled by default.
- 5-minute delay before writing to dead-letter location.
- Dead-letter location unavailable for 4+ hours → event dropped.

## Output Batching

Improves HTTP throughput in high-volume scenarios:

| Setting | Range |
|---------|-------|
| Max events per batch | 1–5,000 |
| Preferred batch size (KB) | configurable ceiling |

## Delayed Delivery

Protects unhealthy endpoints: Event Grid backs off delivery to endpoints experiencing sustained failures.

## Related Pages

- [[azure-event-grid]] — service entity
- [[event-grid-delivery-retry]] — source page
- [[dead-letter-pattern]] — dead-letter concept
