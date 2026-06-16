---
title: "Azure Key Vault"
type: entity
tags: [key-vault, azure, security, secrets, certificates, keys, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_2-key-vault-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Key Vault

## What It Is

Azure Key Vault is a cloud service for securely storing and controlling access to secrets (tokens, passwords, API keys), cryptographic keys, and SSL/TLS certificates. It acts as a centralized secrets manager, removing the need for in-house HSM knowledge and providing high availability through automatic geo-replication.

## Container Types

| Container | Stores |
|-----------|--------|
| **Vault** | Software and HSM-backed keys, secrets, and certificates |
| **Managed HSM pool** | HSM-backed keys only |

## Service Tiers

| Tier | Key Protection |
|------|---------------|
| **Standard** | Software-protected keys |
| **Premium** | HSM-protected keys |

## Core Capabilities

| Capability | Description |
|-----------|-------------|
| Secrets Management | Tokens, passwords, certificates, API keys |
| Key Management | Encryption key creation and control |
| Certificate Management | SSL/TLS certificate provisioning, management, and auto-renewal |

## Authentication

Authentication to Key Vault is handled by [[microsoft-entra-id]]. Authorization via:
- **Azure RBAC** — for vault management AND data access.
- **Key Vault access policy** — for data access only.

Recommended authentication method: [[managed-identity]] (no credential rotation required).

## Data in Transit Encryption

- Enforces **TLS** protocol.
- Uses **Perfect Forward Secrecy (PFS)** with unique per-session keys.
- **RSA-based 2,048-bit** encryption key lengths.

## Operational Best Practices

- One vault per application per environment (Dev / Staging / Production).
- Enable logging and alerts.
- Enable **soft-delete** and **purge protection** to prevent accidental or malicious data loss.
- Create regular backups.

## Role in App Configuration Security

When [[azure-app-configuration]] uses customer-managed keys, it calls Azure Key Vault to wrap/unwrap its encryption key using a managed identity. Requirements:
- Key Vault must have soft-delete and purge-protection enabled.
- An RSA or RSA-HSM key with wrap and unwrap capabilities.
- App Configuration instance must have `GET`, `WRAP`, `UNWRAP` permissions granted in Key Vault access policy.

## Related Pages

- [[managed-identity]] – recommended authentication method
- [[microsoft-entra-id]] – authentication provider
- [[azure-app-configuration]] – complements Key Vault (config vs. secrets)
- [[explore-azure-key-vault]] – overview source
- [[key-vault-best-practices]] – authentication options and best practices
- [[key-vault-authentication]] – detailed auth and REST API
- [[default-azure-credential]] – SDK credential used to authenticate to Key Vault
