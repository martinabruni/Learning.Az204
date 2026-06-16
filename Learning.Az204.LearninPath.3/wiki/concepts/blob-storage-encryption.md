---
title: "Blob Storage Encryption"
type: concept
tags: [blob-storage, encryption, sse, customer-managed-keys, security, fips, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Blob Storage Encryption

## Definition

Azure Blob Storage uses **Service-Side Encryption (SSE)** to automatically encrypt all data at rest. Encryption is always on, cannot be disabled, and incurs no extra cost.

## Encryption at Rest

- Algorithm: **256-bit AES** (strongest available block cipher).
- Compliance: **FIPS 140-2**.
- Analogous to BitLocker encryption on Windows.
- Covers: all blob types, disks, files, queues, tables, and all object metadata.
- Applies regardless of performance tier, access tier, or deployment model.
- Both primary and secondary region data encrypted when geo-replication is enabled.

## Key Management Options

| Option | Who Manages Keys | Supported Services | Key Storage |
|---|---|---|---|
| Microsoft-managed keys (default) | Microsoft | All | Microsoft key store |
| Customer-managed keys (CMK) | Customer | Blob Storage, Azure Files | [[azure-key-vault]] or Key Vault HSM |
| Customer-provided keys | Customer (per request) | Blob Storage | Customer's own key store |

### Customer-Managed Keys

- Stored in [[azure-key-vault]] or Azure Key Vault Managed HSM.
- Customer controls key rotation.
- Can be scoped to account, container, or blob level.

### Customer-Provided Keys

- Client includes an encryption key on individual read/write requests.
- Enables granular per-operation control.
- Not available for Azure Files.

## Client-Side Encryption

Encrypt data **before** uploading to Azure Storage (data never leaves the client unencrypted):

| Version | Mode | SDK Support |
|---|---|---|
| v2 (recommended) | AES-GCM (Galois/Counter Mode) | Blob, Queue Storage |
| v1 | AES-CBC (Cipher Block Chaining) | Blob, Queue, Table Storage |

Available in .NET, Java, and Python client libraries.

## Related Pages

- [[azure-blob-storage]] – entity: the service
- [[azure-key-vault]] – entity: key storage for CMK
- [[blob-storage-security]] – source: full security feature details
- [[blob-access-tiers]] – encryption applies across all tiers
