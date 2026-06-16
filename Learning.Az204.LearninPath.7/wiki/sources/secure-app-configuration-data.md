---
title: "Secure App Configuration Data"
type: source
tags: [app-configuration, azure, security, managed-identity, private-endpoints, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_5-secure-app-configuration-data.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Secure App Configuration Data

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_5-secure-app-configuration-data.pdf

## Overview

[[azure-app-configuration]] supports three mechanisms to secure configuration data:
1. Customer-managed keys
2. Private endpoints
3. Managed identities

## Customer-Managed Keys

By default, App Configuration encrypts sensitive information at rest using a **256-bit AES key** provided by Microsoft (one per App Configuration instance).

When **customer-managed key capability** is enabled:
- App Configuration uses a [[managed-identity]] assigned to the instance to authenticate with [[microsoft-entra-id]].
- The managed identity calls [[azure-key-vault]] and **wraps** the App Configuration encryption key.
- The wrapped key is stored; the unwrapped key is **cached for 1 hour** and refreshed hourly.

### Requirements to Enable Customer-Managed Key

- **Standard tier** App Configuration instance (not Free tier).
- Azure Key Vault with **soft-delete and purge-protection** enabled.
- An RSA or RSA-HSM key in Key Vault: not expired, enabled, with **wrap and unwrap** capabilities.

### Steps to Configure

1. Assign a managed identity to the App Configuration instance.
2. Grant the identity `GET`, `WRAP`, and `UNWRAP` permissions in the Key Vault access policy.

## Private Endpoints

Private endpoints allow clients on a virtual network to securely access App Configuration over a **private link** (using VNet address space IP, traversing Microsoft backbone — no public internet exposure).

Benefits:
- Block all connections on the public endpoint via firewall.
- Prevent data from escaping the virtual network.
- Connect from on-premises networks via VPN or ExpressRoute with private-peering.

## Managed Identities for App Configuration

A [[managed-identity]] from [[microsoft-entra-id]] allows App Configuration to access Microsoft Entra ID-protected resources (e.g., Azure Key Vault).

### Add a System-Assigned Identity

```bash
az appconfig identity assign \
    --name myTestAppConfigStore \
    --resource-group myResourceGroup
```

### Add a User-Assigned Identity

```bash
# Step 1: Create the identity
az identity create --resource-group myResourceGroup --name myUserAssignedIdentity

# Step 2: Assign to App Configuration store
az appconfig identity assign --name myTestAppConfigStore \
    --resource-group myResourceGroup \
    --identities /subscriptions/[subscription id]/resourcegroups/myResourceGroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myUserAssignedIdentity
```

## Key Claims

- One App Configuration instance can have **only one system-assigned identity**, but **multiple user-assigned identities**.
- Customer-managed key encryption requires Standard tier — not available on Free tier.
- The encryption key cache refresh interval is **1 hour**.

## Data Points

- Default encryption: 256-bit AES, Microsoft-managed key.
- Customer-managed key: requires RSA or RSA-HSM key type in Key Vault.

## Related Pages

- [[azure-app-configuration]] – entity page
- [[azure-key-vault]] – used as the key store for customer-managed encryption
- [[managed-identity]] – used by App Configuration to access Key Vault
- [[microsoft-entra-id]] – identity platform
- [[explore-app-configuration]] – service overview
- [[app-configuration-feature-management]] – feature flags
