---
title: "Event Grid Subscriptions and Filtering"
type: concept
tags: [event-grid, subscriptions, filtering, az204]
sources: [event-grid-filtering.md, event-grid-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Event Grid Subscriptions and Filtering

An **event subscription** tells [[azure-event-grid]] which events on a topic a subscriber wants to receive. Subscriptions can filter events to reduce noise and control routing.

## Subscription Components

- **Endpoint**: where events are sent (webhook URL, Azure service resource).
- **Filter**: which events to include.
- **Expiration**: optional; for time-limited subscriptions.
- **Custom headers**: up to 10 HTTP headers per subscription (each ≤ 4,096 bytes).

## Filter Types

### 1. Event Type Filtering

Include only specific event types:
```json
"filter": {
  "includedEventTypes": ["Microsoft.Resources.ResourceWriteSuccess"]
}
```
Use `All` to get every event type.

### 2. Subject Filtering

Filter by subject prefix or suffix:
```json
"filter": {
  "subjectBeginsWith": "/blobServices/default/containers/mycontainer",
  "subjectEndsWith": ".jpg"
}
```

### 3. Advanced Filtering

Filter on event data fields with operators:
```json
"filter": {
  "advancedFilters": [
    { "operatorType": "NumberGreaterThanOrEquals", "key": "Data.Key1", "value": 5 },
    { "operatorType": "StringContains", "key": "Subject", "values": ["container1"] }
  ]
}
```

## Related Pages

- [[azure-event-grid]] — entity
- [[event-grid-filtering]] — source page
- [[event-grid-schema]] — subject path structure
- [[event-grid-delivery-retry-concept]] — delivery and retry
