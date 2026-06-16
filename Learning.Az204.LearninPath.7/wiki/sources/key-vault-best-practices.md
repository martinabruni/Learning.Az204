---
title: "Azure Key Vault Best Practices"
type: source
tags: [key-vault, azure, security, best-practices, tls, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Key Vault Best Practices

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf

## Overview

This unit covers the three authentication methods for [[azure-key-vault]], the encryption protocol used in transit, and operational best practices for vault management.

## Authentication to Key Vault

Three ways to authenticate to Key Vault, ordered by recommendation:

| Method | Recommended? | Notes |
|--------|-------------|-------|
| **Managed identities for Azure resources** | Yes (best practice) | Azure automatically rotates the service principal client secret. No credential management required. |
| **Service principal and certificate** | Not recommended | Application owner/developer must manually rotate the certificate. |
| **Service principal and secret** | Not recommended | Hard to automatically rotate the bootstrap secret. |

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf
> "We recommend this approach [managed identities] as a best practice."

## Encryption of Data in Transit

- [[azure-key-vault]] enforces **TLS** to protect data in transit between Key Vault and clients.
- **Perfect Forward Secrecy (PFS)** protects connections using unique keys per session.
- Connections use **RSA-based 2,048-bit encryption** key lengths.

## Operational Best Practices

| Practice | Detail |
|----------|--------|
| **Use separate key vaults** | One vault per application per environment (Dev, Pre-Prod, Prod); reduces blast radius of a breach |
| **Control access** | Allow only authorized applications and users |
| **Backup** | Create regular backups on update/delete/create of vault objects |
| **Logging** | Turn on logging and alerts |
| **Recovery options** | Enable soft-delete and purge protection to guard against force deletion |

## Key Claims

- A "secret" in Key Vault terms is anything requiring tightly controlled access: API keys, passwords, certificates.
- A "vault" is a logical group of secrets.
- The benefit of managed identity authentication: the app **never manages the rotation of the first secret** — Azure handles the service principal client secret rotation automatically.

## Related Pages

- [[azure-key-vault]] – entity page
- [[explore-azure-key-vault]] – overview and service tiers
- [[key-vault-authentication]] – detailed authentication guide and REST API
- [[managed-identity]] – recommended Key Vault authentication method
