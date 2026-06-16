---
title: "EventProcessorClient"
type: entity
tags: [event-hubs, sdk, event-processor, dotnet, java, az204]
sources: [event-hubs-processing.md, event-hubs-programming-guide.md]
created: 2026-06-16
updated: 2026-06-16
---

# EventProcessorClient

**EventProcessorClient** (and its equivalents) is the recommended production SDK component for reading and processing events from [[azure-event-hubs]].

## SDK Equivalents

| Language | Class |
|----------|-------|
| .NET (v5.0+) | `EventProcessorClient` (Azure.Messaging.EventHubs.Processor) |
| Java (v5.0+) | `EventProcessorClient` |
| Python | `EventHubConsumerClient` |
| JavaScript | `EventHubConsumerClient` |

## Responsibilities

- **Partition ownership**: claims ownership of partitions; evenly distributes load among active instances.
- **Load balancing**: automatically rebalances when instances join or leave.
- **Checkpointing**: persists the position of the last successfully processed event per partition in a checkpoint store.
- **Failure recovery**: on restart, resumes from the last checkpoint.

## Dependencies

- **Checkpoint store**: requires an Azure Blob Storage container (`BlobContainerClient`) for state persistence.

## Usage Pattern (C#)

```csharp
var processor = new EventProcessorClient(blobContainerClient, consumerGroup, eventHubsConnectionString, eventHubName);
processor.ProcessEventAsync += myEventHandler;
processor.ProcessErrorAsync += myErrorHandler;

await processor.StartProcessingAsync();
// ... wait ...
await processor.StopProcessingAsync();

// Always remove handlers to prevent leaks
processor.ProcessEventAsync -= myEventHandler;
processor.ProcessErrorAsync -= myErrorHandler;
```

## Related Pages

- [[azure-event-hubs]] — parent service
- [[event-hubs-processing]] — scaling and processing details
- [[event-hubs-programming-guide]] — code examples
- [[checkpointing-concept]] — checkpointing pattern
- [[partitioned-consumer-pattern]] — underlying scaling model
