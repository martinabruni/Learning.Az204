---
title: "Checkpointing (Event Hubs)"
type: concept
tags: [event-hubs, checkpointing, offset, resiliency, az204]
sources: [event-hubs-processing.md]
created: 2026-06-16
updated: 2026-06-16
---

# Checkpointing (Event Hubs)

**Checkpointing** is the process by which an [[event-processor-client]] marks the position (**offset**) of the last successfully processed event within a partition in [[azure-event-hubs]].

## Purpose

1. **At-least-once semantics**: enables other consumers to resume from where the previous one left off after a failure.
2. **Replay**: specify a lower offset to reprocess older events.
3. **"Mark as complete"**: downstream applications can confirm events have been handled.

## How It Works

1. Event processor writes the current offset to a **checkpoint store** (Azure Blob Storage).
2. If the processor disconnects, another instance queries the store to find the last committed offset.
3. The new instance starts reading from that offset.

## Per-Partition Scope

Checkpoints are maintained **per-partition within a consumer group**. Different consumer groups have independent checkpoint positions.

## Thread Safety Note

The event processing function is called **sequentially per partition** by default. Events from different partitions may be processed concurrently — shared state across partitions must be synchronized.

## Related Pages

- [[azure-event-hubs]] — entity
- [[event-hubs-processing]] — source page
- [[event-processor-client]] — client that manages checkpointing
- [[partitioned-consumer-pattern]] — partition model
