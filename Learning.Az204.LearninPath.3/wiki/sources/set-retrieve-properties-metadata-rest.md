---
title: "Set and Retrieve Properties and Metadata for Blob Resources by Using REST"
type: source
tags: [blob-storage, rest-api, metadata, properties, http, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_6-set-retrieve-properties-metadata-rest.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Set and Retrieve Properties and Metadata for Blob Resources by Using REST

> [!source] learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_6-set-retrieve-properties-metadata-rest.pdf

## Overview

Containers and blobs support custom metadata represented as HTTP headers. Metadata can be set at resource creation time or added/updated later via explicit requests.

## Key Claims

### Metadata Header Format

```
x-ms-meta-name:string-value
```

- From API version 2009-09-19 onwards, metadata names must follow C# identifier naming rules.
- Names are case-insensitive (preserved on creation, but insensitive when set or read).
- Duplicate metadata header names on the same resource → **400 (Bad Request)**.
- Total size of all metadata pairs can be up to **8 KB**.

### Operations on Metadata

- Metadata can be retrieved or set directly without altering or returning the resource content.
- Metadata values can only be read or written **in full** — partial updates are not supported.
- Setting metadata overwrites any existing metadata values on the resource.

### Retrieving Properties and Metadata (GET/HEAD)

GET/HEAD returns headers only (no response body):

```
GET/HEAD https://myaccount.blob.core.windows.net/mycontainer?restype=container&comp=metadata
GET/HEAD https://myaccount.blob.core.windows.net/mycontainer/myblob?comp=metadata
```

### Setting Metadata Headers (PUT)

PUT overwrites all existing metadata. PUT with no headers clears all metadata:

```
PUT https://myaccount.blob.core.windows.net/mycontainer?comp=metadata&restype=container
PUT https://myaccount.blob.core.windows.net/mycontainer/myblob?comp=metadata
```

### Standard HTTP Properties

Properties and metadata are both HTTP headers; they differ in naming:
- **Metadata headers**: `x-ms-meta-` prefix + custom name.
- **Property headers**: standard HTTP header names (per HTTP/1.1 spec section 14).

Standard HTTP headers on **containers**: `ETag`, `Last-Modified`.

Standard HTTP headers on **blobs**: `ETag`, `Last-Modified`, `Content-Length`, `Content-Type`, `Content-MD5`, `Content-Encoding`, `Content-Language`, `Cache-Control`, `Origin`, `Range`.

## Related Pages

- [[blob-properties-metadata]] – concept: system properties and user-defined metadata
- [[manage-container-properties-metadata-dotnet]] – source: .NET SDK approach
- [[azure-blob-storage]] – entity page
- [[blob-storage-resources]] – source: resource types
