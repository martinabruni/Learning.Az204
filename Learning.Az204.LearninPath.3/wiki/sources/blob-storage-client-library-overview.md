---
title: "Explore Azure Blob Storage Client Library"
type: source
tags: [blob-storage, dotnet, client-library, sdk, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_2-blob-storage-client-library-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Blob Storage Client Library

> [!source] learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_2-blob-storage-client-library-overview.pdf

## Overview

The Azure Storage client libraries for .NET offer a convenient interface for making calls to Azure Storage. The latest version is **12.x** — recommended for all new applications.

## Key Claims

### Core Classes

| Class | Description |
|---|---|
| `BlobClient` | Manipulate individual Azure Storage blobs |
| `BlobClientOptions` | Client configuration options for connecting to Blob Storage |
| `BlobContainerClient` | Manipulate containers and their blobs |
| `BlobServiceClient` | Manipulate service resources and blob containers; storage account is top-level namespace |
| `BlobUriBuilder` | Modify URI instances to point to different Azure Storage resources |

### NuGet Packages

- `Azure.Storage.Blobs` — primary classes (client objects) for service, containers, and blobs.
- `Azure.Storage.Blobs.Specialized` — classes for blob-type-specific operations (e.g., block blobs).
- `Azure.Storage.Blobs.Models` — utility classes, structures, and enumeration types.

## Related Pages

- [[azure-blob-storage-sdk]] – concept: .NET SDK for Blob Storage
- [[create-client-object]] – source: creating BlobServiceClient, BlobContainerClient, BlobClient
- [[azure-blob-storage]] – entity page
- [[blob-storage-resources]] – source: resource types (accounts, containers, blobs)
