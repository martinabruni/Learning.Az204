---
title: "Dead-Letter Pattern"
type: concept
tags: [messaging, pattern, dead-letter, reliability, az204]
sources: [event-grid-delivery-retry.md]
created: 2026-06-16
updated: 2026-06-16
---

# Dead-Letter Pattern

The **dead-letter pattern** is a reliability technique in messaging systems where undeliverable messages are routed to a dedicated storage location (the **dead-letter queue** or **dead-letter location**) instead of being silently dropped.

## Purpose

- Prevent message loss when delivery permanently fails.
- Allow operators to inspect, diagnose, and replay failed messages.

## Azure Event Grid Implementation

In [[azure-event-grid]], dead-lettering applies when:
1. Event is not delivered within the **TTL** (time-to-live).
2. Delivery attempt count exceeds the **max attempts** limit.
3. Endpoint returns **400** or **413** (immediate dead-letter scheduling).

### Configuration

- Must be **explicitly enabled** when creating the event subscription.
- Requires specifying an **Azure Blob Storage container** as the dead-letter location.
- 5-minute delay between last delivery attempt and writing to dead-letter location.
- If dead-letter location is unavailable for **4 hours** → event is dropped entirely.

### Default Behavior (Dead-Letter Disabled)

Events that match no-retry error codes (400, 413, 401 for webhooks) are **dropped** if dead-lettering is not configured.

## Related Pages

- [[azure-event-grid]] — entity
- [[event-grid-delivery-retry]] — source page
- [[event-grid-delivery-retry-concept]] — delivery concept
