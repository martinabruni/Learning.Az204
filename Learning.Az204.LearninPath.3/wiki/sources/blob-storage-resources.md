---
title: "Discover Azure Blob Storage Resource Types"
type: source
tags: [blob-storage, containers, blobs, storage-accounts, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_3-blob-storage-resources.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Azure Blob Storage Resource Types

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_3-blob-storage-resources.pdf

## Overview

[[azure-blob-storage]] offers three types of resources forming a hierarchy:
1. The **storage account** — unique namespace in Azure.
2. A **container** in the storage account — organizes blobs like a directory.
3. A **blob** in a container — the actual data object.

## Key Claims

### Storage Accounts

- Every object stored in Azure Storage has an address including the unique account name.
- Default endpoint pattern: `http://<accountname>.blob.core.windows.net`

### Containers

- A container organizes blobs similarly to a directory in a file system.
- A storage account can have an unlimited number of containers.
- A container can store an unlimited number of blobs.
- Container name must be a valid DNS name (forms part of the URI).

**Container naming rules:**
- Between 3 and 63 characters long.
- Must start with a letter or number.
- Can contain only lowercase letters, numbers, and dash (`-`).
- Two or more consecutive dashes are not permitted.

Container URI format: `https://myaccount.blob.core.windows.net/mycontainer`

### Blob Types

| Blob Type | Description | Max Size |
|---|---|---|
| Block blob | Text and binary data; made of individually manageable blocks | ~190.7 TiB |
| Append blob | Optimized for append operations (e.g., logging from VMs) | N/A |
| Page blob | Random access files; stores VHD files for Azure VMs | 8 TB |

Blob URI formats:
- `https://myaccount.blob.core.windows.net/mycontainer/myblob`
- `https://myaccount.blob.core.windows.net/mycontainer/myvirtualdirectory/myblob`

## Related Pages

- [[azure-blob-storage]] – entity page
- [[azure-storage-account]] – top-level namespace
- [[blob-types]] – concept: block, append, page blobs
- [[blob-storage-overview]] – storage account types and access tiers
- [[blob-storage-security]] – security features
