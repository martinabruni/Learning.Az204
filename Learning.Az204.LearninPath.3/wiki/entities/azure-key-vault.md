---
title: "Azure Key Vault"
type: entity
tags: [key-vault, security, encryption, customer-managed-keys, azure, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_4-blob-storage-security.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Key Vault

## What It Is

Azure Key Vault is a cloud service for securely storing and accessing secrets, keys, and certificates. In the context of Azure Blob Storage, it is the required storage location for **customer-managed encryption keys**.

## Role in Blob Storage Encryption

- Customer-managed keys for Azure Blob Storage **must** be stored in Azure Key Vault or Azure Key Vault Managed Hardware Security Model (HSM).
- Enables customers to control key rotation and key scope (account, container, or blob level).
- Supported for Blob Storage and Azure Files encryption.

## Key Vault vs Key Vault HSM

| Option | Description |
|---|---|
| Azure Key Vault | Software-protected key storage |
| Azure Key Vault Managed HSM | Hardware Security Module — higher security, FIPS 140-3 Level 3 validated |

## Related Pages

- [[blob-storage-encryption]] – concept: encryption key management options
- [[blob-storage-security]] – source: security features including key management
- [[azure-blob-storage]] – entity: the service that uses Key Vault for CMK
