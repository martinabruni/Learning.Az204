---
title: "Azure Event Hubs"
type: entity
tags: [azure, event-hubs, streaming, kafka, amqp, az204]
sources: [event-hubs-overview.md, event-hubs-capture.md, event-hubs-processing.md, event-hubs-access-control.md, event-hubs-programming-guide.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Event Hubs

**Azure Event Hubs** is a native cloud **data-streaming service** capable of ingesting millions of events per second with low latency. It acts as the "front door" for an event pipeline (also called an event ingestor).

## Key Facts

| Property | Value |
|----------|-------|
| Type | Fully managed PaaS |
| Throughput | Millions of events/second |
| Protocols | AMQP 1.0, Apache Kafka, HTTPS |
| Data format (Capture) | Apache Avro |
| Standard TUs | 1–40 per namespace (auto-inflate supported) |
| Ingress per TU | Up to 1 MB/s or ~1,000 1-KB events/s |
| Egress per TU | Up to 2 MB/s or 4,096 events/s |

## Core Components

| Component | Role |
|-----------|------|
| Namespace | Management container for event hubs; handles capacity, security, geo-DR |
| Event Hub / Kafka topic | Append-only distributed log with one or more partitions |
| Partitions | Parallelism and scaling mechanism |
| Consumer group | Logical group of consumers reading independently |
| Schema Registry | Centralized schema management (free with namespace) |

## Key Features

- **Apache Kafka compatibility**: run Kafka workloads without code changes.
- **Event Hubs Capture**: auto-save streams to Azure Blob Storage or ADLS in Avro format.
- **Stream Analytics integration**: real-time SQL-based stream processing.
- **EventProcessorClient**: production-grade event processing with load balancing and checkpointing.

## Authentication and Authorization

| Method | Details |
|--------|---------|
| Microsoft Entra ID (RBAC) | Data Owner, Data Sender, Data Receiver roles |
| SAS (publishers) | Unique token per client; one publisher per client |
| SAS (consumers) | Manage or listen rights at namespace/event hub level |

## RBAC Roles

| Role | Permission |
|------|------------|
| Azure Event Hubs Data Owner | Full access |
| Azure Event Hubs Data Sender | Send only |
| Azure Event Hubs Data Receiver | Receive only |

## Related Pages

- [[event-hubs-overview]] — overview and components
- [[event-hubs-capture]] — automatic data capture
- [[event-hubs-processing]] — scaling and event processor
- [[event-hubs-access-control]] — security and RBAC
- [[event-hubs-programming-guide]] — SDK code examples
- [[partitioned-consumer-pattern]] — core scaling pattern
- [[apache-kafka]] — Kafka compatibility
- [[event-processor-client]] — EventProcessorClient
