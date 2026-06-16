---
title: "Explore Event Hubs Capture"
type: source
tags: [event-hubs, capture, avro, storage, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-hubs_3-event-hubs-capture.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Event Hubs Capture

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-hubs_3-event-hubs-capture.pdf

## Overview

[[azure-event-hubs]] Capture automatically saves streaming data to **Azure Blob Storage** or **Azure Data Lake Storage** with configurable time or size intervals. Setup is fast, has no administrative overhead, and scales automatically.

> "Event Hubs Capture enables you to process real-time and batch-based pipelines on the same stream."

## Key Claims

- Captured data written in **Apache Avro format** (compact, binary, with inline schema).
- Storage account can be in same or different region as the event hub.
- Capture runs automatically once configured; writes **empty files** when no data is available (for predictable batch processing cadence).
- Capture copies data directly from internal Event Hubs storage, bypassing TU egress — preserving egress for other readers (e.g., Stream Analytics, Spark).
- Standard tier: 1–40 throughput units (TUs) per namespace; auto-inflate available.

## How Capture Works

Event Hubs is a **time-retention durable buffer** (like a distributed log). Each partition is independent and consumed independently. Data ages off based on the configurable retention period.

You specify:
- Azure Blob Storage account + container, **or** Azure Data Lake Store account.

## Capture Windowing

A minimum size and time configuration with a **"first wins policy"** — whichever trigger (time or size) fires first causes a capture. Each partition captures independently and writes a completed block blob.

### Storage Naming Convention

```
{Namespace}/{EventHub}/{PartitionId}/{Year}/{Month}/{Day}/{Hour}/{Minute}/{Second}
```

Example:
```
https://mystorageaccount.blob.core.windows.net/mycontainer/mynamespace/myeventhub/0/2017/12/08/03/03/17.avro
```

## Throughput Units (TUs)

| Metric | Value |
|--------|-------|
| Ingress per TU | Up to 1 MB/s (or ~1,000 1-KB events/s) |
| Egress per TU | Up to 2 MB/s (or 4,096 events/s) |
| Standard namespace range | 1–40 TUs |

Usage beyond purchased TUs is **throttled**.

## Related Pages

- [[azure-event-hubs]] — entity page
- [[event-hubs-overview]] — general overview
- [[apache-avro]] — Avro format concept
- [[azure-blob-storage]] — storage destination entity
- [[azure-data-lake-storage]] — alternative storage destination
