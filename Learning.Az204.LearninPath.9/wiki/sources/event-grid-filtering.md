---
title: "Filter Events (Event Grid)"
type: source
tags: [event-grid, filtering, subscriptions, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_7-event-grid-filtering.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Filter Events (Event Grid)

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_7-event-grid-filtering.pdf

## Overview

When creating an [[azure-event-grid]] event subscription, three filtering options are available:

1. **Event type filtering**
2. **Subject filtering** (begins with / ends with)
3. **Advanced filtering** (field values and operators)

## Event Type Filtering

By default, all event types are sent. Use `includedEventTypes` to restrict:

```json
"filter": {
  "includedEventTypes": [
    "Microsoft.Resources.ResourceWriteFailure",
    "Microsoft.Resources.ResourceWriteSuccess"
  ]
}
```

Specify `All` to receive all event types.

## Subject Filtering

Filter by prefix or suffix of the event subject:

```json
"filter": {
  "subjectBeginsWith": "/blobServices/default/containers/mycontainer/log",
  "subjectEndsWith": ".jpg"
}
```

Use cases:
- `subjectEndsWith: ".txt"` → only text file upload events.
- `subjectBeginsWith: "/blobServices/default/containers/testcontainer"` → all events for a specific container.

## Advanced Filtering

Filter by values in the event data fields using comparison operators:

```json
"filter": {
  "advancedFilters": [
    {
      "operatorType": "NumberGreaterThanOrEquals",
      "key": "Data.Key1",
      "value": 5
    },
    {
      "operatorType": "StringContains",
      "key": "Subject",
      "values": ["container1", "container2"]
    }
  ]
}
```

Advanced filter components:
- `operatorType`: comparison type (e.g., `NumberGreaterThanOrEquals`, `StringContains`).
- `key`: field in the event data (number, boolean, or string).
- `value` / `values`: value(s) to compare against.

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-overview]] — core concepts
- [[event-grid-schema]] — event structure and subject paths
- [[event-grid-subscriptions]] — subscription concept page
