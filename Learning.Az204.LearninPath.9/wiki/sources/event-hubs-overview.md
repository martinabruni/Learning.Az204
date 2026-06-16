---
title: "Discover Azure Event Hubs"
type: source
tags: [event-hubs, streaming, kafka, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-hubs_2-event-hubs-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Azure Event Hubs

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-hubs_2-event-hubs-overview.pdf

## Overview

[[azure-event-hubs]] is a native cloud data-streaming service capable of streaming **millions of events per second** with low latency. It is compatible with **Apache Kafka**, enabling existing Kafka workloads to run without code changes.

> "Azure Event Hubs is a native data-streaming service in the cloud that can stream millions of events per second, with low latency, from any source to any destination."

## Key Claims

- Compatible with Apache Kafka — no code changes required for Kafka workloads.
- Uses a **partitioned consumer model** to enable concurrent processing by multiple applications.
- Integrates with Azure Functions for serverless architectures.
- Supports AMQP 1.0 protocol natively.
- SDKs available in .NET, Java, Python, JavaScript.

## Key Capabilities

### Apache Kafka on Azure Event Hubs
Natively supports AMQP, Apache Kafka, and HTTPS protocols. No need to manage your own Kafka clusters.

### Schema Registry in Event Hubs
Centralized repository for managing schemas of event streaming applications. Comes free with every Event Hubs namespace. Compatible with Kafka and Event Hubs SDK applications.

### Real-time Processing with Stream Analytics
Integration with Azure Stream Analytics for real-time stream processing. Includes a no-code drag-and-drop editor and a SQL-based query language.

## Key Components

| Component | Description |
|-----------|-------------|
| **Producer applications** | Ingest data using Event Hubs SDKs or any Kafka producer client |
| **Namespace** | Management container for one or more event hubs or Kafka topics; handles capacity, security, geo-DR |
| **Event Hub / Kafka topic** | Append-only distributed log; can have one or more partitions |
| **Partitions** | Scaling mechanism; like lanes in a freeway — more partitions = more throughput |
| **Consumer applications** | Read from the event log; maintain consumer offset |
| **Consumer group** | Logical group of consumer instances reading from an event hub independently at their own pace |

## Related Pages

- [[azure-event-hubs]] — entity page
- [[event-hubs-capture]] — automatic data capture
- [[event-hubs-processing]] — scaling event processing
- [[apache-kafka]] — Kafka compatibility concept
- [[partitioned-consumer-pattern]] — partitioned consumer model
