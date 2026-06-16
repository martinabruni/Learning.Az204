---
title: "Wiki Activity Log – AZ-204 Learning Path 3"
type: synthesis
tags: [log, az204, blob-storage]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log — AZ-204 Learning Path 3

---

## [2026-06-16] ingest | Explore Azure Blob Storage (Module 1 — 3 PDFs)
- Added: blob-storage-overview.md, blob-storage-resources.md, blob-storage-security.md
- Added entities: azure-blob-storage.md, azure-storage-account.md, azure-key-vault.md
- Added concepts: blob-access-tiers.md, blob-types.md, blob-storage-encryption.md
- Key takeaways: Blob Storage is Microsoft's unstructured object storage with a three-tier resource hierarchy (account → container → blob); four access tiers (Hot/Cool/Cold/Archive) optimize cost vs access speed; encryption is always on with 256-bit AES; three key management options available (Microsoft-managed, customer-managed via Key Vault, customer-provided per request)

## [2026-06-16] ingest | Manage Azure Blob Storage Lifecycle (Module 2 — 4 PDFs)
- Added: blob-storage-lifecycle.md, blob-lifecycle-policies.md, add-policy-blob-storage.md, rehydrate-blob-data.md
- Added concepts: blob-lifecycle-management.md
- Updated entities: azure-blob-storage.md (added lifecycle management section)
- Key takeaways: Lifecycle management uses a JSON policy (up to 100 rules) with filter sets and action sets to automatically transition blobs between tiers or delete them based on age; when multiple actions apply, the least expensive wins; archive blobs are offline and require rehydration (up to 15 hours standard, under 1 hour high priority); Set Blob Tier rehydration has a caution — doesn't update last modified time, which can trigger re-archival by an active lifecycle policy

## [2026-06-16] ingest | Work with Azure Blob Storage (Module 3 — 4 PDFs)
- Added: blob-storage-client-library-overview.md, create-client-object.md, manage-container-properties-metadata-dotnet.md, set-retrieve-properties-metadata-rest.md
- Added entities: microsoft-entra-id.md
- Added concepts: azure-blob-storage-sdk.md, blob-properties-metadata.md
- Key takeaways: The .NET SDK v12 provides a hierarchy of client objects (BlobServiceClient → BlobContainerClient → BlobClient) authenticated via DefaultAzureCredential with Microsoft Entra ID and Azure RBAC; containers and blobs support system properties (standard HTTP headers) and user-defined metadata (x-ms-meta- prefix, max 8 KB total); metadata must be read/written in full — no partial updates via .NET or REST
