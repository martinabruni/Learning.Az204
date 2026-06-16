---
title: "Explore Azure Blob Storage"
type: source
tags: [blob-storage, storage-accounts, access-tiers, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Blob Storage

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf

## Overview

[[azure-blob-storage]] is Microsoft's object storage solution for the cloud, optimized for storing massive amounts of unstructured data (text or binary data).

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf
> "Azure Blob storage is Microsoft's object storage solution for the cloud. Blob storage is optimized for storing massive amounts of unstructured data."

## Key Claims

- Blob storage is accessed via HTTP/HTTPS from anywhere in the world.
- Objects are accessible via Azure Storage REST API, Azure PowerShell, Azure CLI, or an Azure Storage client library.
- An Azure Storage account is the top-level container for all Blob storage and provides a unique namespace.

## Designed For

- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming video and audio.
- Writing to log files.
- Backup, restore, disaster recovery, and archiving.
- Data analysis by on-premises or Azure-hosted services.

## Types of Storage Accounts

| Account Type | Services | Redundancy | Use Case |
|---|---|---|---|
| Standard general-purpose v2 | Blob, Queue, Table, Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS | Recommended for most scenarios |
| Premium block blobs | Blob (incl. Data Lake Storage) | LRS, ZRS | High transaction rates, small objects, low latency |
| Premium file shares | Azure Files | LRS, ZRS | Enterprise/high-performance file shares |
| Premium page blobs | Page blobs only | LRS, ZRS | Page blobs only |

## Access Tiers for Block Blob Data

| Tier | Min Storage Duration | Characteristics |
|---|---|---|
| Hot | None (default) | Highest storage cost, lowest access cost |
| Cool | 30 days | Lower storage cost, higher access cost |
| Cold | 90 days | Lower storage cost than Cool, higher access cost |
| Archive | 180 days | Offline; cheapest storage, most expensive access; hours of retrieval latency |

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf
> "The Archive tier, which is available only for individual block blobs. The archive tier is optimized for data that can tolerate several hours of retrieval latency and remains in the Archive tier for a minimum 180 days."

Access tiers can be switched at any time based on usage pattern changes.

## Related Pages

- [[azure-blob-storage]] – entity page
- [[azure-storage-account]] – the top-level container
- [[blob-access-tiers]] – concept: Hot, Cool, Cold, Archive tiers
- [[blob-storage-resources]] – resource types (accounts, containers, blobs)
- [[blob-storage-security]] – encryption and security features
