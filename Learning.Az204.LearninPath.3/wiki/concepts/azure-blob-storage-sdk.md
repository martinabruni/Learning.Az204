---
title: "Azure Blob Storage SDK (.NET)"
type: concept
tags: [blob-storage, dotnet, sdk, client-library, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_2-blob-storage-client-library-overview.pdf,
          learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_3-create-client-object.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Blob Storage SDK (.NET)

## Definition

The Azure Storage client library for .NET (version 12.x) provides a hierarchical set of client objects for interacting with Azure Blob Storage resources.

## Client Hierarchy

```
BlobServiceClient  (storage account level)
  └── BlobContainerClient  (container level)
        └── BlobClient  (individual blob level)
```

Each level provides methods scoped to that resource.

## Core Classes

| Class | Scope | Key Operations |
|---|---|---|
| `BlobServiceClient` | Storage account | List/create/delete containers; account properties |
| `BlobContainerClient` | Container | Create/delete/configure container; list/upload/delete blobs; properties and metadata |
| `BlobClient` | Individual blob | Upload, download, delete, metadata operations on a single blob |
| `BlobClientOptions` | Configuration | Client options for connection |
| `BlobUriBuilder` | URI manipulation | Modify URIs to point to different resources |

## NuGet Packages

| Package | Purpose |
|---|---|
| `Azure.Storage.Blobs` | Primary client objects |
| `Azure.Storage.Blobs.Specialized` | Type-specific operations (e.g., block blobs) |
| `Azure.Storage.Blobs.Models` | Utility classes, structures, enumerations |

## Authentication Pattern

Uses `DefaultAzureCredential` from `Azure.Identity`:

```csharp
BlobServiceClient client = new(
    new Uri($"https://{accountName}.blob.core.windows.net"),
    new DefaultAzureCredential());
```

Security principal must have appropriate **Azure RBAC role** (e.g., Storage Blob Data Contributor).

## Version

- **Version 12.x** is the current recommended version for new applications.

## Related Pages

- [[microsoft-entra-id]] – authentication via DefaultAzureCredential
- [[azure-blob-storage]] – entity: the service
- [[blob-storage-client-library-overview]] – source: classes and packages
- [[create-client-object]] – source: code examples for creating clients
- [[manage-container-properties-metadata-dotnet]] – source: properties/metadata .NET usage
