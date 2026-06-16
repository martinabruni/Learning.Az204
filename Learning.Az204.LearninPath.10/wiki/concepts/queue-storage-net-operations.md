---
title: "Queue Storage .NET Operation Patterns"
type: concept
tags: [queue-storage, dotnet, sdk, az204, patterns]
sources: [queue-storage-dotnet.md]
created: 2026-06-16
updated: 2026-06-16
---

# Queue Storage .NET Operation Patterns

## Overview

[[azure-queue-storage]] is managed via the `QueueClient` class from the `Azure.Storage.Queues` NuGet package. This concept page documents the key operation patterns.

## Two-Step Dequeue (At-Least-Once Processing)

The most important pattern for reliable message processing:

1. `ReceiveMessages()` — message becomes **invisible for 30 seconds** (default); returned to caller.
2. Process the message within the visibility window.
3. `DeleteMessage(messageId, popReceipt)` — permanently removes the message.

If step 3 is not called (e.g., due to a crash), the message **reappears** after the visibility timeout and can be retried.

> This mirrors the Peek Lock pattern in [[service-bus-receive-modes]].

## Extending Processing Time

Use `UpdateMessage(messageId, popReceipt, content, visibilityTimeout)` to:
- Update message content in-place.
- Extend the visibility timeout (e.g., add 60 more seconds).
- Save intermediate work state on the message.

## Peek Without Consuming

`PeekMessages()` allows inspecting messages without affecting their visibility or state. Useful for monitoring queue contents.

## Queue Length Estimation

`GetProperties().ApproximateMessagesCount` returns an approximate count:
- Not lower than the actual count.
- May be slightly higher due to eventual consistency.

## Key NuGet Packages

| Package | Role |
|---------|------|
| `Azure.Storage.Queues` | Queue operations |
| `Azure.Storage.Common` | Shared infrastructure |
| `Azure.Core` | SDK primitives |
| `System.Configuration.ConfigurationManager` | Read connection strings from config |

## Related Pages

- [[azure-queue-storage]] – entity page
- [[queue-storage-dotnet]] – source document with code snippets
- [[service-bus-receive-modes]] – analogous peek-lock pattern in Service Bus
