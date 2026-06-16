---
title: "Azure Storage Account"
type: entity
tags: [blob-storage, storage-account, azure, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_3-blob-storage-resources.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Storage Account

## What It Is

An Azure Storage account is the **top-level container** for all Azure Blob Storage. It provides a unique namespace for Azure Storage data, accessible globally over HTTP or HTTPS.

## Endpoint Format

```
https://<accountname>.blob.core.windows.net
```

The combination of the account name and the blob endpoint forms the base address for all objects in the storage account.

## Account Types

| Type | Services | Redundancy Options |
|---|---|---|
| Standard general-purpose v2 | Blob, Queue, Table, Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS |
| Premium block blobs | Blob (incl. Data Lake Storage) | LRS, ZRS |
| Premium file shares | Azure Files | LRS, ZRS |
| Premium page blobs | Page blobs only | LRS, ZRS |

## Key Characteristics

- Provides unlimited containers; each container provides unlimited blobs.
- Data storage limits set at the **account level** (not per tier).
- Encryption is enabled for all accounts by default and cannot be disabled.
- Lifecycle management policies apply at the account level (with container/prefix scoping available).

## Related Pages

- [[azure-blob-storage]] – Blob Storage service that uses this account
- [[blob-access-tiers]] – access tiers configurable at account level
- [[blob-lifecycle-management]] – lifecycle policies scoped to storage accounts
- [[blob-storage-overview]] – source: storage account types table
- [[blob-storage-resources]] – source: resource hierarchy
