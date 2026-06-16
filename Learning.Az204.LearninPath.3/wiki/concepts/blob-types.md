---
title: "Blob Types"
type: concept
tags: [blob-storage, block-blob, append-blob, page-blob, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_3-blob-storage-resources.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Blob Types

## Definition

Azure Blob Storage supports three distinct types of blobs, each optimized for different workloads.

## Block Blob

- Stores **text and binary data**.
- Made up of blocks that can be managed individually.
- Maximum size: ~**190.7 TiB**.
- The default and most commonly used blob type.
- Supported by all lifecycle management tiering actions.

## Append Blob

- Made up of blocks like block blobs, but **optimized for append operations**.
- Ideal for scenarios such as **logging data from virtual machines**.
- Once a block is added, it cannot be modified.
- Lifecycle management supports the `delete` action on append blobs.

## Page Blob

- Stores **random access files** up to **8 TB** in size.
- Used to store **Virtual Hard Drive (VHD) files** for Azure virtual machines.
- Optimized for frequent random read/write operations.

## URI Patterns

```
# Blob directly in container
https://myaccount.blob.core.windows.net/mycontainer/myblob

# Blob in virtual directory
https://myaccount.blob.core.windows.net/mycontainer/myvirtualdirectory/myblob
```

## Lifecycle Management Support

| Action | Block Blob | Append Blob | Page Blob |
|---|---|---|---|
| tierToCool | Yes | No | No |
| tierToCold | Yes | No | No |
| tierToArchive | Yes | No | No |
| delete | Yes | Yes | No |

## Related Pages

- [[azure-blob-storage]] – entity page
- [[blob-storage-resources]] – source: resource types
- [[blob-lifecycle-management]] – concept: lifecycle policies per blob type
- [[blob-access-tiers]] – tiering applies to block blobs only
