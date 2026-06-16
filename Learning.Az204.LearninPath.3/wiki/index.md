---
title: "Wiki Index – AZ-204 Learning Path 3: Azure Blob Storage"
type: synthesis
tags: [index, az204, blob-storage]
sources: [blob-storage-overview.md, blob-storage-resources.md, blob-storage-security.md,
          blob-storage-lifecycle.md, blob-lifecycle-policies.md, add-policy-blob-storage.md,
          rehydrate-blob-data.md, blob-storage-client-library-overview.md, create-client-object.md,
          manage-container-properties-metadata-dotnet.md, set-retrieve-properties-metadata-rest.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 3: Azure Blob Storage

This wiki is built from 11 PDFs in `raw/`, covering three Microsoft Learn modules on Azure Blob Storage.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-blob-storage]] | Microsoft's object storage for unstructured data; three resource levels: account, container, blob |
| [[azure-storage-account]] | Top-level namespace for all Blob Storage; unique endpoint per account |
| [[azure-key-vault]] | Secure key storage required for customer-managed encryption keys |
| [[microsoft-entra-id]] | Identity service used for SDK authentication via DefaultAzureCredential |

---

## Concepts

| Page | Summary |
|------|---------|
| [[blob-access-tiers]] | Hot, Cool, Cold, Archive tiers — each trades storage cost for access cost |
| [[blob-types]] | Three blob types: block (text/binary), append (log workloads), page (VHD/random access) |
| [[blob-storage-encryption]] | SSE with 256-bit AES always enabled; three key management options |
| [[blob-lifecycle-management]] | Rule-based JSON policy for automated tier transitions and data expiration |
| [[azure-blob-storage-sdk]] | .NET SDK v12 client hierarchy: BlobServiceClient → BlobContainerClient → BlobClient |
| [[blob-properties-metadata]] | System properties (HTTP headers) and user-defined metadata (x-ms-meta- prefix) |

---

## Sources — Module 1: Explore Azure Blob Storage

| Page | PDF |
|------|-----|
| [[blob-storage-overview]] | `explore-azure-blob-storage_2-blob-storage-overview.pdf` |
| [[blob-storage-resources]] | `explore-azure-blob-storage_3-blob-storage-resources.pdf` |
| [[blob-storage-security]] | `explore-azure-blob-storage_4-blob-storage-security.pdf` |

## Sources — Module 2: Manage Azure Blob Storage Lifecycle

| Page | PDF |
|------|-----|
| [[blob-storage-lifecycle]] | `manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf` |
| [[blob-lifecycle-policies]] | `manage-azure-blob-storage-lifecycle_3-blob-storage-lifecycle-policies.pdf` |
| [[add-policy-blob-storage]] | `manage-azure-blob-storage-lifecycle_4-add-policy-blob-storage.pdf` |
| [[rehydrate-blob-data]] | `manage-azure-blob-storage-lifecycle_5-rehydrate-blob-data.pdf` |

## Sources — Module 3: Work with Azure Blob Storage

| Page | PDF |
|------|-----|
| [[blob-storage-client-library-overview]] | `work-azure-blob-storage_2-blob-storage-client-library-overview.pdf` |
| [[create-client-object]] | `work-azure-blob-storage_3-create-client-object.pdf` |
| [[manage-container-properties-metadata-dotnet]] | `work-azure-blob-storage_5-manage-container-properties-metadata-dotnet.pdf` |
| [[set-retrieve-properties-metadata-rest]] | `work-azure-blob-storage_6-set-retrieve-properties-metadata-rest.pdf` |

---

## Page Counts

- Sources: 11
- Entities: 4
- Concepts: 6
- **Total wiki pages: 21** (plus this index and log.md)
