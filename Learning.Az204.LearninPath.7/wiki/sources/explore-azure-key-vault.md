---
title: "Explore Azure Key Vault"
type: source
tags: [key-vault, azure, security, secrets, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_2-key-vault-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Key Vault

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_2-key-vault-overview.pdf

## Overview

[[azure-key-vault]] is a cloud service for securely storing and controlling access to secrets, keys, and certificates. It supports two types of containers:

- **Vaults** — store software and HSM-backed keys, secrets, and certificates.
- **Managed HSM pools** — support HSM-backed keys only.

## Problems Key Vault Solves

| Area | Description |
|------|-------------|
| **Secrets Management** | Securely store and control access to tokens, passwords, certificates, API keys |
| **Key Management** | Create and control encryption keys used to encrypt data |
| **Certificate Management** | Provision, manage, and deploy SSL/TLS certificates for Azure and internal resources |

## Service Tiers

| Tier | Protection |
|------|-----------|
| **Standard** | Software-key encryption |
| **Premium** | HSM-protected keys |

## Key Benefits

- **Centralized application secrets**: Store connection strings in Key Vault rather than app code; applications access secrets via versioned URIs.
- **Securely store secrets and keys**: Authentication via [[microsoft-entra-id]]; authorization via Azure RBAC or Key Vault access policy.
  - Azure RBAC: used for vault management AND data access.
  - Key Vault access policy: used only for data access.
- **Monitor access and use**: Enable logging; stream to Event Hub, archive to Storage, or send to Azure Monitor logs.
- **Simplified administration**: 
  - No in-house HSM knowledge required.
  - Data replication within and across regions (high availability, automatic failover).
  - Certificate automation (enrollment and renewal for Public CA certificates).

## Key Quotes

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_2-key-vault-overview.pdf
> "Instead of storing the connection string in the app's code you can store it securely in Key Vault. Your applications can securely access the information they need by using URIs."

## Related Pages

- [[azure-key-vault]] – entity page
- [[key-vault-best-practices]] – best practices and authentication methods
- [[key-vault-authentication]] – authentication details and REST API
- [[managed-identity]] – recommended authentication method for Key Vault
