---
title: "Manage Container Properties and Metadata by Using .NET"
type: source
tags: [blob-storage, dotnet, metadata, properties, client-library, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_5-manage-container-properties-metadata-dotnet.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Manage Container Properties and Metadata by Using .NET

> [!source] learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_5-manage-container-properties-metadata-dotnet.pdf

## Overview

Blob containers support two types of associated data beyond their content: **system properties** and **user-defined metadata**.

## Key Claims

### System Properties vs User-Defined Metadata

| Type | Description |
|---|---|
| System properties | Exist on each Blob Storage resource; some read/write, some read-only; correspond to standard HTTP headers; managed by the .NET client library |
| User-defined metadata | One or more name-value pairs specified by the developer; stored with the resource but don't affect behavior |

- Metadata name/value pairs are valid HTTP headers.
- Metadata names must be valid HTTP header names and valid C# identifiers.
- Only ASCII characters; case-insensitive.
- Non-ASCII metadata values should be Base64-encoded or URL-encoded.

### Retrieving Container Properties

Use `BlobContainerClient` methods:
- `GetProperties()` / `GetPropertiesAsync()`

```csharp
var properties = await container.GetPropertiesAsync();
Console.WriteLine($"Public access level: {properties.Value.PublicAccess}");
Console.WriteLine($"Last modified time in UTC: {properties.Value.LastModified}");
```

### Setting Metadata

Use `BlobContainerClient` methods:
- `SetMetadata()` / `SetMetadataAsync()`

```csharp
IDictionary<string, string> metadata = new Dictionary<string, string>();
metadata.Add("docType", "textDocuments");
metadata.Add("category", "guidance");
await container.SetMetadataAsync(metadata);
```

- If two or more metadata headers with the same name are submitted, the Blob service returns status code **400 (Bad Request)**.

### Retrieving Metadata

Metadata is retrieved via the same `GetProperties` / `GetPropertiesAsync` methods:

```csharp
var properties = await container.GetPropertiesAsync();
foreach (var metadataItem in properties.Value.Metadata)
{
    Console.WriteLine($"Key: {metadataItem.Key}, Value: {metadataItem.Value}");
}
```

## Related Pages

- [[blob-properties-metadata]] – concept: system properties and user-defined metadata
- [[set-retrieve-properties-metadata-rest]] – source: REST API approach
- [[create-client-object]] – source: creating client objects
- [[azure-blob-storage-sdk]] – concept: .NET SDK for Blob Storage
- [[azure-blob-storage]] – entity page
