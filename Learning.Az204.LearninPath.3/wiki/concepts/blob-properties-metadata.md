---
title: "Blob Properties and Metadata"
type: concept
tags: [blob-storage, metadata, properties, http-headers, rest, dotnet, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_5-manage-container-properties-metadata-dotnet.pdf,
          learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_6-set-retrieve-properties-metadata-rest.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Blob Properties and Metadata

## Definition

Blob containers and blobs support two types of associated data beyond their content:

| Type | Description | HTTP Header Prefix |
|---|---|---|
| System properties | Read-only or read/write; correspond to standard HTTP headers; managed by the client library | Standard HTTP header names |
| User-defined metadata | One or more custom name-value pairs; stored with the resource; no effect on resource behavior | `x-ms-meta-` |

## Metadata Rules

- Names must be valid HTTP header names **and** valid C# identifiers.
- Only ASCII characters allowed; case-insensitive.
- Non-ASCII values must be Base64-encoded or URL-encoded.
- Total metadata size limit: **8 KB**.
- Duplicate metadata names on a resource → **400 (Bad Request)**.
- Metadata is read/written **in full** — partial updates are not supported.
- Setting metadata **overwrites** all existing metadata on the resource.

## Standard HTTP Properties

**Containers**: `ETag`, `Last-Modified`

**Blobs**: `ETag`, `Last-Modified`, `Content-Length`, `Content-Type`, `Content-MD5`, `Content-Encoding`, `Content-Language`, `Cache-Control`, `Origin`, `Range`

## .NET SDK Operations

| Operation | Method |
|---|---|
| Get container properties | `BlobContainerClient.GetPropertiesAsync()` |
| Set container metadata | `BlobContainerClient.SetMetadataAsync(IDictionary)` |
| Get container metadata | `BlobContainerClient.GetPropertiesAsync()` (same call; returns both) |

## REST API Operations

| Operation | HTTP Method | URI Pattern |
|---|---|---|
| Get container metadata | GET/HEAD | `.../{container}?restype=container&comp=metadata` |
| Get blob metadata | GET/HEAD | `.../{container}/{blob}?comp=metadata` |
| Set container metadata | PUT | `.../{container}?comp=metadata&restype=container` |
| Set blob metadata | PUT | `.../{container}/{blob}?comp=metadata` |

PUT with no headers **clears all existing metadata**.

## Related Pages

- [[manage-container-properties-metadata-dotnet]] – source: .NET SDK code examples
- [[set-retrieve-properties-metadata-rest]] – source: REST API patterns
- [[azure-blob-storage-sdk]] – concept: .NET client library
- [[azure-blob-storage]] – entity page
