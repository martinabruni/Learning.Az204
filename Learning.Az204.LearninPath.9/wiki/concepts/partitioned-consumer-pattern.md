---
title: "Partitioned Consumer Pattern"
type: concept
tags: [event-hubs, pattern, scaling, parallelism, az204]
sources: [event-hubs-overview.md, event-hubs-processing.md]
created: 2026-06-16
updated: 2026-06-16
---

# Partitioned Consumer Pattern

The **partitioned consumer pattern** is the core scaling mechanism of [[azure-event-hubs]]. It enables high-throughput parallel processing by assigning partitions to individual consumers.

> "The key to scale for Event Hubs is the idea of partitioned consumers. In contrast to the competing consumers pattern, the partitioned consumer pattern enables high scale by removing the contention bottleneck and facilitating end to end parallelism."

## How It Works

- An event hub is divided into **partitions** (like lanes on a freeway).
- Each partition is an independent, append-only segment of the event stream.
- Each consumer in a **consumer group** reads from one or more specific partitions.
- Multiple consumer groups can independently read the same stream at their own pace.

## Benefits

| Benefit | Description |
|---------|-------------|
| No contention | Each partition is owned by one consumer at a time |
| Parallelism | Multiple consumers process different partitions simultaneously |
| Independent pace | Consumer groups don't interfere with each other |
| Horizontal scale | Add more partitions and more consumer instances to scale up |

## Contrast with Competing Consumers

| Pattern | Behavior |
|---------|----------|
| Competing consumers | Multiple consumers share a queue; each message processed once |
| Partitioned consumers | Each partition owned by one consumer; all messages in a partition processed sequentially by that consumer |

## Consumer Group

A **consumer group** is a logical view of the event stream. Each consumer group maintains its own **offset** (position in the stream), enabling different applications to read the same data independently.

## Related Pages

- [[azure-event-hubs]] — entity
- [[event-hubs-overview]] — components overview
- [[event-hubs-processing]] — EventProcessorClient scaling
- [[checkpointing-concept]] — tracking position
- [[pub-sub-pattern]] — related messaging pattern
