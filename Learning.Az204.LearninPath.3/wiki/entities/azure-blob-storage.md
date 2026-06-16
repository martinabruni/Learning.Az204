---
title: "Azure Blob Storage"
type: entity
tags: [blob-storage, azure, storage, paas, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_3-blob-storage-resources.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Blob Storage

## What It Is

Azure Blob Storage is Microsoft's **object storage solution for the cloud**, optimized for storing massive amounts of **unstructured data** (text or binary). It is accessible globally via HTTP/HTTPS.

## Resource Hierarchy

```
Storage Account  →  Container(s)  →  Blob(s)
```

- **Storage Account**: top-level namespace; endpoint: `https://<account>.blob.core.windows.net`
- **Container**: organizes blobs like a directory; unlimited containers per account
- **Blob**: the data object; three types available

## Blob Types

| Type | Max Size | Best For |
|---|---|---|
| Block blob | ~190.7 TiB | Text and binary data; most common type |
| Append blob | N/A | Append-only workloads (e.g., log files, VM logging) |
| Page blob | 8 TB | Random access; VHD files for Azure VMs |

## Access Tiers

| Tier | Min Duration | Pattern |
|---|---|---|
| Hot | None | Frequent access (default) |
| Cool | 30 days | Infrequent access |
| Cold | 90 days | Rarely accessed |
| Archive | 180 days | Offline; hours to rehydrate |

## Security

- All data encrypted at rest with 256-bit AES (FIPS 140-2); always on; no extra cost.
- Key management options: Microsoft-managed, customer-managed (Azure Key Vault), customer-provided.
- Client-side encryption available via .NET, Java, Python SDKs.

## Storage Account Types

- **Standard general-purpose v2**: recommended for most scenarios.
- **Premium block blobs**: high transaction rates, low latency.
- **Premium file shares**: enterprise file shares.
- **Premium page blobs**: VHD/page blob workloads.

## Related Pages

- [[azure-storage-account]] – the top-level container entity
- [[blob-access-tiers]] – Hot, Cool, Cold, Archive tiers concept
- [[blob-types]] – block, append, page blob types
- [[blob-lifecycle-management]] – automated tiering and expiration
- [[blob-storage-encryption]] – SSE and key management
- [[azure-blob-storage-sdk]] – .NET client library
- [[blob-properties-metadata]] – system properties and user metadata
- [[blob-storage-overview]] – source: overview and storage account types
- [[blob-storage-resources]] – source: resource types
- [[blob-storage-security]] – source: security features
