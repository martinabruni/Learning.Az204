---
title: "Scale Your Processing Application (Event Hubs)"
type: source
tags: [event-hubs, event-processor, checkpointing, scaling, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-hubs_4-event-processing.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Scale Your Processing Application (Event Hubs)

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-hubs_4-event-processing.pdf

## Overview

[[azure-event-hubs]] supports scalable event processing by running multiple consumer instances that balance the load among themselves. The recommended client depends on SDK version and language.

> "The key to scale for Event Hubs is the idea of partitioned consumers. In contrast to the competing consumers pattern, the partitioned consumer pattern enables high scale by removing the contention bottleneck and facilitating end to end parallelism."

## Client Libraries by Version

| SDK / Language | Older versions | Newer versions (5.0+) |
|----------------|---------------|----------------------|
| .NET, Java | `EventProcessorHost` | `EventProcessorClient` |
| Python, JavaScript | — | `EventHubConsumerClient` |

## Example Scenario

Home security company with 100,000 homes, each with multiple sensors pushing data to an event hub (16 partitions). Consumers must:

1. **Scale**: each consumer reads from a few partitions.
2. **Load balance**: dynamically increase/decrease consumers as event volume changes.
3. **Seamless resume on failure**: if consumer A fails, others pick up its partitions and resume from the last checkpoint.
4. **Consume events**: aggregate and upload to blob storage.

## Partition Ownership Tracking

- Each event processor instance owns and processes events from one or more partitions.
- Ownership is **evenly distributed** among active instances.
- Each processor has a unique identifier and records ownership in a **checkpoint store**.
- All instances periodically update the store and learn about other active instances for load balancing.

## Receive Messages

- Each call to the process-event function delivers **a single event** from a specific partition.
- For at-least-once processing: add retry logic in your code (beware of poisoned messages).
- Recommendation: do as little processing per event as possible. Use **two consumer groups** if you need to write to storage and do routing.

## Checkpointing

Process by which an event processor **marks the position of the last successfully processed event** within a partition.

- Done per-partition within a consumer group.
- On reconnect: processor passes offset to Event Hub to resume from the checkpoint.
- Enables both "mark as complete" semantics and resiliency.
- Can specify a lower offset to replay older data.

## Thread Safety

- Function processing events is called **sequentially for a given partition** by default.
- Subsequent events from the same partition queue up in the background.
- Events from **different partitions** can be processed concurrently → shared state must be synchronized.

## Related Pages

- [[azure-event-hubs]] — entity page
- [[event-hubs-overview]] — overview and key components
- [[partitioned-consumer-pattern]] — scaling pattern concept
- [[event-processor-client]] — EventProcessorClient entity
- [[checkpointing-concept]] — checkpointing pattern
