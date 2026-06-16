---
title: "Azure Queue Storage"
type: entity
tags: [queue-storage, azure-storage, az204, messaging, async]
sources: [azure-queue-storage-overview.md, queue-storage-dotnet.md, choose-queue-solution.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Queue Storage

## What It Is

Azure Queue Storage is an **Azure Storage service** for storing large numbers of messages. It is accessed via authenticated HTTP or HTTPS calls from anywhere in the world. It is primarily used to create **backlogs of work** for asynchronous processing.

## Key Specifications

| Property | Value |
|----------|-------|
| Max message size | 64 KB |
| Queue capacity | Millions of messages (up to storage account limit) |
| Max queue size | Over 80 GB |
| Default message TTL | 7 days |
| Max message TTL (API ≥ 2017-07-29) | Unlimited (set to -1) |
| Access | HTTP / HTTPS authenticated calls |
| Queue name format | All lowercase |

## URL Format

```
https://<storage-account>.queue.core.windows.net/<queue>
```

## Components

- **Storage Account**: Gateway to all Azure Storage services.
- **Queue**: Named container for messages (lowercase name required).
- **Message**: Payload up to 64 KB, with configurable TTL.

## .NET SDK Operations

Key operations via `QueueClient`:

| Operation | Method |
|-----------|--------|
| Create queue | `CreateIfNotExists()` |
| Send message | `SendMessage(message)` |
| Peek message | `PeekMessages()` |
| Receive message | `ReceiveMessages()` |
| Update message | `UpdateMessage(id, popReceipt, content, timeout)` |
| Delete message | `DeleteMessage(id, popReceipt)` |
| Get queue length | `GetProperties()` → `ApproximateMessagesCount` |
| Delete queue | `Delete()` |

## When to Choose Queue Storage (vs Service Bus)

See [[choose-queue-solution]] for the full decision guide. Key triggers:
- Need to store more than 80 GB of messages
- Need to track per-message processing progress (resumable after crash)
- Need server-side transaction logs

## Related Pages

- [[azure-queue-storage-overview]] – overview source
- [[queue-storage-dotnet]] – .NET code examples source
- [[azure-service-bus]] – alternative enterprise messaging service
- [[choose-queue-solution]] – decision guide source
- [[queue-storage-net-operations]] – concept: .NET operation patterns
- [[azure-storage-account]] – Azure Storage Account entity
