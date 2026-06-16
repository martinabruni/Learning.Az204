---
title: "Wiki Activity Log – AZ-204 Learning Path 9"
type: synthesis
tags: [log, az204, event-grid, event-hubs]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log — AZ-204 Learning Path 9

Append-only chronological log of all wiki activity.

---

## [2026-06-16] ingest | Azure Event Grid – Overview (Unit 2)
- Added: sources/event-grid-overview.md
- Updated: entities/azure-event-grid.md (created), wiki/index.md (created)
- Key takeaways: Event Grid is a managed Pub/Sub service supporting HTTP and MQTT; supports push and pull delivery; conforms to CloudEvents 1.0; max event size 1 MB.

## [2026-06-16] ingest | Azure Event Grid – Event Schemas (Unit 3)
- Added: sources/event-grid-schema.md
- Updated: concepts/cloudevents-spec.md (created)
- Key takeaways: Two schema types (Event Grid schema and CloudEvents v1.0); array max 1 MB; 413 on oversize; events charged in 64-KB increments; subject path enables hierarchical filtering.

## [2026-06-16] ingest | Azure Event Grid – Event Delivery Durability (Unit 4)
- Added: sources/event-grid-delivery-retry.md, concepts/event-grid-delivery-retry-concept.md, concepts/dead-letter-pattern.md
- Key takeaways: At-least-once delivery; exponential backoff; 30 max attempts / 1440-min TTL defaults; dead-letter requires explicit storage account; output batching up to 5,000 events/batch; custom HTTP headers up to 10 per subscription.

## [2026-06-16] ingest | Azure Event Grid – Access Control (Unit 5)
- Added: sources/event-grid-access-control.md, concepts/event-grid-security.md, concepts/azure-rbac.md
- Key takeaways: Four built-in RBAC roles; non-WebHook handlers require EventSubscriptions/Write permission; scope differs between system and custom topics.

## [2026-06-16] ingest | Azure Event Grid – Webhook Event Delivery (Unit 6)
- Added: sources/event-grid-webhook-delivery.md, concepts/webhook-validation-pattern.md
- Key takeaways: Ownership validation required; Logic Apps/Automation/Functions auto-validated; sync handshake with validationCode; async handshake with validationUrl (5-min window); self-signed certs not supported.

## [2026-06-16] ingest | Azure Event Grid – Event Filtering (Unit 7)
- Added: sources/event-grid-filtering.md, concepts/event-grid-subscriptions.md
- Key takeaways: Three filter types: event type, subject (begins/ends with), advanced (field operators); advanced filters support NumberGreaterThanOrEquals, StringContains, and other operators.

## [2026-06-16] ingest | Azure Event Hubs – Overview (Unit 2)
- Added: sources/event-hubs-overview.md
- Updated: entities/azure-event-hubs.md (created)
- Key takeaways: Native cloud streaming service; Kafka-compatible (no code changes); AMQP 1.0 + Kafka + HTTPS; Schema Registry free with namespace; Stream Analytics integration; partitioned consumer model.

## [2026-06-16] ingest | Azure Event Hubs – Capture (Unit 3)
- Added: sources/event-hubs-capture.md
- Key takeaways: Auto-capture to Azure Blob Storage or ADLS in Apache Avro format; "first wins" windowing policy; storage naming convention includes namespace/eventhub/partition/datetime; Capture bypasses TU egress; 1–40 TUs per standard namespace.

## [2026-06-16] ingest | Azure Event Hubs – Event Processing / Scaling (Unit 4)
- Added: sources/event-hubs-processing.md, concepts/partitioned-consumer-pattern.md, concepts/checkpointing-concept.md
- Updated: entities/event-processor-client.md (created)
- Key takeaways: EventProcessorClient (.NET/Java) and EventHubConsumerClient (Python/JS) for production; partition ownership tracked via checkpoint store (Azure Blob); checkpointing per partition per consumer group; sequential processing per partition, concurrent across partitions.

## [2026-06-16] ingest | Azure Event Hubs – Authentication & Authorization (Unit 5)
- Added: sources/event-hubs-access-control.md, concepts/shared-access-signatures.md
- Updated: concepts/azure-rbac.md, entities/microsoft-entra-id.md (created)
- Key takeaways: Entra ID + RBAC (Data Owner/Sender/Receiver roles); SAS for publishers (one unique token per client) and consumers (manage/listen at entity level); Entra ID preferred — no credentials in code.

## [2026-06-16] ingest | Azure Event Hubs – Programming Guide (Unit 6)
- Added: sources/event-hubs-programming-guide.md
- Updated: entities/event-processor-client.md
- Key takeaways: EventHubProducerClient for inspect/publish; EventHubConsumerClient for exploratory reads; EventProcessorClient for production reads (requires BlobContainerClient); always remove event handlers after StopProcessingAsync.
