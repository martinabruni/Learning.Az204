---
title: "Perform Common Operations with the Event Hubs Client Library"
type: source
tags: [event-hubs, sdk, dotnet, programming, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-hubs_6-event-hubs-programming-guide.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Perform Common Operations with the Event Hubs Client Library

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-hubs_6-event-hubs-programming-guide.pdf

## Overview

Common operations using the **Azure.Messaging.EventHubs** NuGet package in C#.

## Inspect Event Hubs (Get Partition IDs)

```csharp
var connectionString = "<< CONNECTION STRING FOR THE EVENT HUBS NAMESPACE >>";
var eventHubName = "<< NAME OF THE EVENT HUB >>";

await using (var producer = new EventHubProducerClient(connectionString, eventHubName))
{
    string[] partitionIds = await producer.GetPartitionIdsAsync();
}
```

Partition names are assigned at creation time; query to discover them.

## Publish Events

Use `EventHubProducerClient`. Recommended: **automatic routing** (no specific partition specified) for high availability and even distribution.

```csharp
await using (var producer = new EventHubProducerClient(connectionString, eventHubName))
{
    using EventDataBatch eventBatch = await producer.CreateBatchAsync();
    eventBatch.TryAdd(new EventData(new BinaryData("First")));
    eventBatch.TryAdd(new EventData(new BinaryData("Second")));
    await producer.SendAsync(eventBatch);
}
```

## Read Events (All Partitions)

Use `EventHubConsumerClient` with `ReadEventsAsync`. **For exploration and prototyping only** — not recommended for production.

```csharp
string consumerGroup = EventHubConsumerClient.DefaultConsumerGroupName;
await using (var consumer = new EventHubConsumerClient(consumerGroup, connectionString, eventHubName))
{
    using var cancellationSource = new CancellationTokenSource();
    cancellationSource.CancelAfter(TimeSpan.FromSeconds(45));

    await foreach (PartitionEvent receivedEvent in consumer.ReadEventsAsync(cancellationSource.Token))
    {
        // process event
    }
}
```

## Read Events from a Specific Partition

```csharp
string consumerGroup = EventHubConsumerClient.DefaultConsumerGroupName;
await using (var consumer = new EventHubConsumerClient(consumerGroup, connectionString, eventHubName))
{
    EventPosition startingPosition = EventPosition.Earliest;
    string partitionId = (await consumer.GetPartitionIdsAsync()).First();

    using var cancellationSource = new CancellationTokenSource();
    cancellationSource.CancelAfter(TimeSpan.FromSeconds(45));

    await foreach (PartitionEvent receivedEvent in
        consumer.ReadEventsFromPartitionAsync(partitionId, startingPosition, cancellationSource.Token))
    {
        // process event
    }
}
```

## Process Events with EventProcessorClient (Production)

**Recommended for production**. Requires Azure Blob Storage for checkpoint persistence.

```csharp
var storageClient = new BlobContainerClient(storageConnectionString, blobContainerName);
var processor = new EventProcessorClient(storageClient, consumerGroup, eventHubsConnectionString, eventHubName);

processor.ProcessEventAsync += processEventHandler;
processor.ProcessErrorAsync += processErrorHandler;

await processor.StartProcessingAsync();
// ... wait for cancellation ...
await processor.StopProcessingAsync();

// Remove handlers to prevent leaks
processor.ProcessEventAsync -= processEventHandler;
processor.ProcessErrorAsync -= processErrorHandler;
```

Key points:
- `EventProcessorClient` manages partition ownership, load balancing, and checkpointing.
- Requires `BlobContainerClient` for state persistence.
- Always remove event handlers after stopping to prevent memory leaks.

## Related Pages

- [[azure-event-hubs]] — entity page
- [[event-hubs-overview]] — overview
- [[event-hubs-processing]] — scaling and checkpointing
- [[event-processor-client]] — EventProcessorClient entity
