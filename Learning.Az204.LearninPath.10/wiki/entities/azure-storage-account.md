---
title: "Azure Storage Account"
type: entity
tags: [azure-storage, storage-account, az204]
sources: [azure-queue-storage-overview.md, queue-storage-dotnet.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Storage Account

## What It Is

An Azure Storage Account is the **gateway to all Azure Storage services**, including Blob Storage, File Storage, Table Storage, and Queue Storage. All access to Azure Storage goes through a storage account.

## Relevance to Queue Storage

- A storage account hosts one or more [[azure-queue-storage]] queues.
- The storage account name forms part of the queue URL: `https://<account>.queue.core.windows.net/<queue>`.
- The queue capacity is bounded by the total capacity limit of the storage account.
- The connection string for accessing queues is retrieved from the storage account.

## Related Pages

- [[azure-queue-storage]] – Queue Storage service hosted in this account
- [[azure-queue-storage-overview]] – Queue Storage overview source
- [[queue-storage-dotnet]] – .NET SDK examples using connection strings
