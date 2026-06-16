---
title: "Create a Client Object"
type: source
tags: [blob-storage, dotnet, client-library, sdk, authentication, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_3-create-client-object.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Create a Client Object

> [!source] learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_3-create-client-object.pdf

## Overview

Working with any Azure resource using the .NET SDK begins with creating a client object. Client objects are created by passing a URI referencing the endpoint to the client constructor. Authentication uses `DefaultAzureCredential` (Microsoft Entra security principal).

## Key Claims

### Authentication

- Code samples use `DefaultAzureCredential` to authenticate via Microsoft Entra security principal.
- The authentication process obtains an access token passed as a credential when the client is instantiated.
- The credential persists throughout the client lifetime.
- The Entra security principal must be assigned an appropriate **Azure RBAC role** granting access to blob data.

### BlobServiceClient

- Top-level client for interacting at the **storage account level**.
- Provides methods to retrieve/configure account properties, and list/create/delete containers.

```csharp
using Azure.Identity;
using Azure.Storage.Blobs;

public BlobServiceClient GetBlobServiceClient(string accountName)
{
    BlobServiceClient client = new(
        new Uri($"https://{accountName}.blob.core.windows.net"),
        new DefaultAzureCredential());
    return client;
}
```

### BlobContainerClient

- Interacts with a **specific container resource**.
- Provides methods to create, delete, configure a container, and list/upload/delete blobs within it.
- Can be created from `BlobServiceClient` or directly (for narrowly scoped work).

```csharp
// From BlobServiceClient
BlobContainerClient client = blobServiceClient.GetBlobContainerClient(containerName);

// Direct creation
BlobContainerClient client = new(
    new Uri($"https://{accountName}.blob.core.windows.net/{containerName}"),
    new DefaultAzureCredential(), clientOptions);
```

### BlobClient

- Interacts with a **specific blob resource**.
- Created from a service client or container client.

```csharp
BlobClient client =
    blobServiceClient.GetBlobContainerClient(containerName).GetBlobClient(blobName);
```

## Related Pages

- [[azure-blob-storage-sdk]] – concept: .NET SDK client hierarchy
- [[blob-storage-client-library-overview]] – source: SDK classes overview
- [[manage-container-properties-metadata-dotnet]] – source: properties/metadata with .NET
- [[azure-blob-storage]] – entity page
- [[microsoft-entra-id]] – authentication via DefaultAzureCredential
