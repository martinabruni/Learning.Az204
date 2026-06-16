---
title: "Discover Event Schemas"
type: source
tags: [event-grid, schema, cloudevents, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_3-event-grid-schema.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Event Schemas

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_3-event-grid-schema.pdf

## Overview

[[azure-event-grid]] supports two event schema types: **Event Grid event schema** and **CloudEvents schema**. All events share four required string properties; the `data` object is publisher-specific.

## Key Claims

- Array of events posted to a topic: max total size **1 MB**.
- Individual event max size: **1 MB**.
- Size limit violation returns **HTTP 413 Payload Too Large**.
- Operations charged in **64 KB increments** (a 130 KB event = 3 charges).
- Event Grid delivers events to subscribers as **an array with a single event**.

## Event Grid Schema Structure

```json
[
  {
    "topic": "string",
    "subject": "string",
    "id": "string",
    "eventType": "string",
    "eventTime": "string",
    "data": { "object-unique-to-each-publisher" },
    "dataVersion": "string",
    "metadataVersion": "string"
  }
]
```

### Required Properties

| Property | Required | Description |
|----------|----------|-------------|
| `subject` | Yes | Publisher-defined path to the event subject |
| `eventType` | Yes | One of the registered event types |
| `eventTime` | Yes | UTC time when the event occurred |
| `id` | Yes | Unique identifier for the event |
| `topic` | No | Full resource path (Event Grid stamps if omitted) |
| `data` | No | Resource-provider-specific data |
| `dataVersion` | No | Schema version of data (publisher-defined) |
| `metadataVersion` | No | Schema version of metadata (Event Grid-defined) |

## Subject Filtering via Path

Publishers should define hierarchical subjects for easy filtering:
- Three-segment path like `/A/B/C` — subscribers can filter broadly (`/A`) or narrowly (`/A/B`).
- Storage example: `/blobServices/default/containers/<name>/blobs/<file>` — subscribers can filter by container or file extension (`.txt`).

## CloudEvents Schema

[[azure-event-grid]] natively supports **CloudEvents v1.0** JSON format via HTTP protocol binding.

Benefits: uniform tooling, standard routing, universal deserialization, cross-platform integration.

Example Azure Blob Storage event in CloudEvents format:
```json
{
  "specversion": "1.0",
  "type": "Microsoft.Storage.BlobCreated",
  "source": "/subscriptions/{id}/resourceGroups/{rg}/providers/Microsoft.Storage/storageAccounts/{account}",
  "id": "9aeb0fdf-c01e-0131-0922-9eb54906e209",
  "time": "2019-11-18T15:13:39.4589254Z",
  "subject": "blobServices/default/containers/{container}/blobs/{file}",
  "data": { "api": "PutBlockList", "blobType": "BlockBlob" }
}
```

Content-type header differences:
- CloudEvents: `application/cloudevents+json; charset=utf-8`
- Event Grid schema: `application/json; charset=utf-8`

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-overview]] — concepts and structure
- [[cloudevents-spec]] — CloudEvents 1.0 standard
- [[event-grid-filtering]] — filtering by subject and event type
