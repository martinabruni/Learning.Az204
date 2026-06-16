---
title: "Explore Azure Queue Storage"
type: source
tags: [queue-storage, azure-storage, az204, messaging]
sources: [learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_7-azure-queue-storage-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Queue Storage

> [!source] learn.microsoft.com_en-us_training_modules_discover-azure-message-queue_7-azure-queue-storage-overview.pdf

## Overview

[[azure-queue-storage]] is a service for storing **large numbers of messages**, accessible from anywhere via authenticated HTTP or HTTPS calls. It is commonly used to create a **backlog of work** for asynchronous processing.

## Key Data Points

- **Max message size**: 64 KB.
- **Queue capacity**: Millions of messages, up to the total capacity of the storage account.
- **Message TTL (before 2017-07-29)**: Maximum 7 days.
- **Message TTL (2017-07-29 and later)**: Any positive number, or `-1` (never expires). Default is 7 days if omitted.

## Queue Service Components

| Component | Description |
|-----------|-------------|
| Storage Account | All access to Azure Storage goes through a storage account |
| Queue | Container for messages; name must be **all lowercase** |
| Message | Any format; up to 64 KB |

## URL Format

Queues are addressable at:

```
https://<storage-account>.queue.core.windows.net/<queue>
```

Example:
```
https://myaccount.queue.core.windows.net/images-to-download
```

## Related Pages

- [[azure-queue-storage]] – entity page
- [[queue-storage-dotnet]] – .NET code examples source
- [[choose-queue-solution]] – decision guide: when to use Queue Storage vs Service Bus
- [[azure-storage-account]] – Azure Storage Account entity
