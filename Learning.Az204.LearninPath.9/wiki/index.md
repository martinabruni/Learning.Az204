---
title: "Wiki Index – AZ-204 Learning Path 9: Azure Event Grid & Azure Event Hubs"
type: synthesis
tags: [index, az204, event-grid, event-hubs]
sources: [event-grid-overview.md, event-hubs-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 9: Azure Event Grid & Azure Event Hubs

This wiki is built from 11 PDFs in `raw/`, covering two Microsoft Learn modules: Azure Event Grid and Azure Event Hubs.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-event-grid]] | Fully managed Pub/Sub message distribution service using HTTP and MQTT |
| [[azure-event-hubs]] | Native cloud data-streaming service; Kafka-compatible; millions of events/second |
| [[event-processor-client]] | Production SDK component for reading and processing Event Hubs events with load balancing and checkpointing |
| [[microsoft-entra-id]] | Microsoft's cloud identity platform; used for OAuth 2.0 authorization in Event Hubs |

---

## Concepts

| Page | Summary |
|------|---------|
| [[pub-sub-pattern]] | Messaging pattern decoupling publishers from subscribers via a topic broker |
| [[cloudevents-spec]] | CNCF open standard for describing event data; supported natively by Event Grid |
| [[event-grid-delivery-retry-concept]] | Durable delivery with exponential backoff, configurable retry policy, and dead-lettering |
| [[event-grid-security]] | Azure RBAC roles and permission scopes for Event Grid operations |
| [[webhook-validation-pattern]] | Ownership validation handshake required before Event Grid delivers events to webhooks |
| [[event-grid-subscriptions]] | Event subscription structure and three filtering options (type, subject, advanced) |
| [[partitioned-consumer-pattern]] | Core Event Hubs scaling model: partition ownership enabling end-to-end parallelism |
| [[checkpointing-concept]] | Tracking the last processed event offset per partition for resiliency and replay |
| [[shared-access-signatures]] | SAS tokens for publisher and consumer authorization in Event Hubs |
| [[azure-rbac]] | Azure role-based access control; built-in roles for Event Grid and Event Hubs |
| [[dead-letter-pattern]] | Routing undeliverable events to a storage account instead of dropping them |

---

## Sources — Module: Azure Event Grid

| Page | PDF |
|------|-----|
| [[event-grid-overview]] | `azure-event-grid_2-event-grid-overview.pdf` |
| [[event-grid-schema]] | `azure-event-grid_3-event-grid-schema.pdf` |
| [[event-grid-delivery-retry]] | `azure-event-grid_4-event-grid-delivery-retry.pdf` |
| [[event-grid-access-control]] | `azure-event-grid_5-authorize-access-event-grid.pdf` |
| [[event-grid-webhook-delivery]] | `azure-event-grid_6-webhook-event-delivery.pdf` |
| [[event-grid-filtering]] | `azure-event-grid_7-event-grid-filtering.pdf` |

## Sources — Module: Azure Event Hubs

| Page | PDF |
|------|-----|
| [[event-hubs-overview]] | `azure-event-hubs_2-event-hubs-overview.pdf` |
| [[event-hubs-capture]] | `azure-event-hubs_3-event-hubs-capture.pdf` |
| [[event-hubs-processing]] | `azure-event-hubs_4-event-processing.pdf` |
| [[event-hubs-access-control]] | `azure-event-hubs_5-event-hubs-authentication-authorization.pdf` |
| [[event-hubs-programming-guide]] | `azure-event-hubs_6-event-hubs-programming-guide.pdf` |

---

## Page Counts

- Sources: 11
- Entities: 4
- Concepts: 11
- **Total wiki pages: 26** (plus this index and log.md)
