---
title: "Explore Azure Storage Security Features"
type: source
tags: [blob-storage, security, encryption, sse, customer-managed-keys, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Storage Security Features

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf

## Overview

[[azure-blob-storage]] uses **service-side encryption (SSE)** to automatically encrypt data when persisted to the cloud. All data at rest is protected by default at no extra cost.

## Key Claims

### Encryption at Rest

- Data encrypted/decrypted transparently using **256-bit AES** encryption (one of the strongest block ciphers available).
- FIPS 140-2 compliant.
- Comparable to BitLocker encryption on Windows.
- Encryption is **enabled for all storage accounts and cannot be disabled**.
- Applies regardless of performance tier, access tier, or deployment model.
- Covers block blobs, append blobs, page blobs (including archive tier), queues, tables, files, disks, and all object metadata.
- Both primary and secondary region data is encrypted when geo-replication is enabled.

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf
> "Azure Storage encryption is enabled for all storage accounts and can't be disabled. Because your data is secured by default, you don't need to modify your code or applications to take advantage of Azure Storage encryption."

### Encryption Key Management

Three options for managing encryption keys:

| Parameter | Microsoft-managed keys | Customer-managed keys | Customer-provided keys |
|---|---|---|---|
| Encryption/decryption | Azure | Azure | Azure |
| Services supported | All | Blob Storage, Azure Files | Blob Storage |
| Key storage | Microsoft key store | Azure Key Vault or Key Vault HSM | Customer's own key store |
| Key rotation responsibility | Microsoft | Customer | Customer |
| Key control | Microsoft | Customer | Customer |
| Key scope | Account, container, or blob | Account, container, or blob | N/A |

- **Customer-managed keys** must be stored in Azure Key Vault or Azure Key Vault Managed Hardware Security Model (HSM).
- **Customer-provided keys** allow per-request granular control on blob read/write operations.

### Client-Side Encryption

- Supported by Azure Blob Storage client libraries for .NET, Java, and Python.
- Queue Storage client libraries for .NET and Python also support client-side encryption.
- Two versions available:
  - **Version 2**: Uses Galois/Counter Mode (GCM) with AES — supported by Blob Storage and Queue Storage SDKs.
  - **Version 1**: Uses Cipher Block Chaining (CBC) with AES — supported by Blob, Queue, and Table Storage SDKs.

## Related Pages

- [[azure-blob-storage]] – entity page
- [[blob-storage-encryption]] – concept: SSE and key management
- [[azure-key-vault]] – entity: key storage for customer-managed keys
- [[blob-storage-overview]] – storage account types
- [[blob-storage-resources]] – resource types
