---
title: "CloudEvents 1.0 Specification"
type: concept
tags: [cloudevents, schema, interoperability, cncf, az204]
sources: [event-grid-overview.md, event-grid-schema.md]
created: 2026-06-16
updated: 2026-06-16
---

# CloudEvents 1.0 Specification

**CloudEvents** is an open specification from the **Cloud Native Computing Foundation (CNCF)** for describing event data in a common way. It aims to improve interoperability across cloud providers and systems.

## Purpose

- Uniform tooling across platforms.
- Standard ways of routing and handling events.
- Universal deserialization of the outer event schema.

## Core Fields

| Field | Description |
|-------|-------------|
| `specversion` | CloudEvents spec version (e.g., `"1.0"`) |
| `type` | Event type (e.g., `"com.yourcompany.order.created"`) |
| `source` | URI identifying the event origin |
| `id` | Unique event identifier |
| `time` | Timestamp in RFC 3339 format |
| `subject` | Optional; subject of the event within the source |
| `datacontenttype` | Content type of the `data` field |
| `data` | Event payload |

## Example

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

## Azure Event Grid and CloudEvents

[[azure-event-grid]] natively supports CloudEvents v1.0 (HTTP binding, JSON format) for both input and output. It can also transform events between Event Grid schema and CloudEvents schema on the wire.

Content-type header: `application/cloudevents+json; charset=utf-8`.

## Related Pages

- [[azure-event-grid]] — uses CloudEvents 1.0
- [[event-grid-schema]] — schema details and comparison
- [[event-grid-overview]] — Event Grid overview
