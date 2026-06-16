---
title: "Create and Manage Azure Queue Storage and Messages by Using .NET"
type: source
tags: [queue-storage, dotnet, csharp, az204, sdk, code-examples]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_8-queue-storage-code-examples.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Create and Manage Azure Queue Storage and Messages by Using .NET

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_8-queue-storage-code-examples.pdf

## Overview

This unit covers the .NET SDK approach to creating and managing queues and messages in [[azure-queue-storage]].

## Required NuGet Packages

| Package | Purpose |
|---------|---------|
| `Azure.Core` | Shared primitives, abstractions, helpers for .NET Azure SDK |
| `Azure.Storage.Common` | Infrastructure shared by Azure Storage client libraries |
| `Azure.Storage.Queues` | Working with Azure Queue Storage |
| `System.Configuration.ConfigurationManager` | Access to configuration files |

## Key Class: QueueClient

The `QueueClient` class is the primary entry point for queue operations.

```csharp
QueueClient queueClient = new QueueClient(connectionString, queueName);
```

## Operations

### Create a Queue

```csharp
QueueClient queueClient = new QueueClient(connectionString, queueName);
queueClient.CreateIfNotExists();
```

### Insert a Message

- Use `SendMessage(message)`.
- Message can be a **string (UTF-8)** or a **byte array**.

```csharp
queueClient.CreateIfNotExists();
if (queueClient.Exists())
{
    queueClient.SendMessage(message);
}
```

### Peek at the Next Message

- Use `PeekMessages()` — does **not** remove the message from the queue.
- Default: peeks at one message. Pass `maxMessages` to peek at more.

```csharp
PeekedMessage[] peekedMessage = queueClient.PeekMessages();
```

### Change the Contents of a Queued Message

- Use `UpdateMessage(messageId, popReceipt, newContent, visibilityTimeout)`.
- Sets a new visibility timeout (e.g., 60 seconds) to extend processing time.
- Useful for saving work-in-progress state on a message.

### Dequeue (Receive and Delete) — Two-Step Process

1. Call `ReceiveMessages()` — message becomes **invisible for 30 seconds** by default.
2. Call `DeleteMessage(messageId, popReceipt)` after successful processing.

> "This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again."

```csharp
QueueMessage[] retrievedMessage = queueClient.ReceiveMessages();
Console.WriteLine($"Dequeued message: '{retrievedMessage[0].Body}'");
queueClient.DeleteMessage(retrievedMessage[0].MessageId, retrievedMessage[0].PopReceipt);
```

### Get the Queue Length

- Use `GetProperties()` → `ApproximateMessagesCount`.
- The count is **not lower than** the actual count but may be higher.

```csharp
QueueProperties properties = queueClient.GetProperties();
int cachedMessagesCount = properties.ApproximateMessagesCount;
```

### Delete a Queue

- Use `Delete()` — removes the queue and all its messages.

```csharp
queueClient.Delete();
```

## Key Takeaways

- The **30-second default invisibility timeout** on `ReceiveMessages` enables at-least-once processing.
- Always call `DeleteMessage` after processing to permanently remove the message.
- `UpdateMessage` can extend visibility to prevent timeout during long-running processing.

## Related Pages

- [[azure-queue-storage]] – entity page
- [[azure-queue-storage-overview]] – Queue Storage overview source
- [[queue-storage-net-operations]] – concept: Queue Storage .NET operation patterns
- [[choose-queue-solution]] – decision guide
