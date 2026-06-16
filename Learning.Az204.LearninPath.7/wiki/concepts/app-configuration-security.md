---
title: "App Configuration Security"
type: concept
tags: [app-configuration, security, customer-managed-keys, private-endpoints, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_5-secure-app-configuration-data.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# App Configuration Security

## Overview

[[azure-app-configuration]] provides three layers of security controls:

1. **Customer-managed keys** — bring-your-own encryption key via Azure Key Vault.
2. **Private endpoints** — restrict network access to a VNet.
3. **Managed identities** — credential-free access to other Azure services.

## Customer-Managed Keys

### Default Behavior

Every App Configuration instance is encrypted at rest with a **256-bit AES key** managed by Microsoft (one key per instance).

### Customer-Managed Key Flow

When enabled:
1. App Configuration uses a [[managed-identity]] to authenticate with [[microsoft-entra-id]].
2. The managed identity calls [[azure-key-vault]] to **wrap** the App Configuration encryption key.
3. Wrapped key is stored; unwrapped key is cached in App Configuration for **1 hour** (refreshed hourly).

### Requirements

| Component | Requirement |
|-----------|------------|
| App Configuration tier | **Standard** (not Free) |
| Azure Key Vault | Soft-delete and purge-protection enabled |
| Key type | RSA or RSA-HSM; not expired; enabled; wrap+unwrap capabilities |
| Identity permissions | `GET`, `WRAP`, `UNWRAP` on Key Vault access policy |

## Private Endpoints

Private endpoints assign the App Configuration store an IP from the **VNet address space**. Traffic flows over the Microsoft backbone — not the public internet.

Benefits:
- Block public endpoint via firewall.
- Prevent data exfiltration from VNet.
- Support on-premises access via VPN or ExpressRoute with private-peering.

## Managed Identities on App Configuration

App Configuration supports both identity types:

| Type | Limit | Lifecycle |
|------|-------|-----------|
| System-assigned | 1 per store | Deleted with store |
| User-assigned | Multiple per store | Independent lifecycle |

## Related Pages

- [[azure-app-configuration]] – entity page
- [[azure-key-vault]] – used for customer-managed key wrapping
- [[managed-identity]] – used by App Configuration to access Key Vault
- [[secure-app-configuration-data]] – full source page
- [[key-vault-access-control]] – Key Vault authorization model
