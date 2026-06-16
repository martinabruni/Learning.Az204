---
title: "Azure App Configuration"
type: entity
tags: [app-configuration, azure, feature-flags, configuration, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_2-app-configuration-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_3-keys-values.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_4-app-configuration-feature-management.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_5-secure-app-configuration-data.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure App Configuration

## What It Is

Azure App Configuration is a fully managed Azure service for centrally managing application settings and feature flags. It complements [[azure-key-vault]] (which stores secrets) by providing a home for non-secret configuration data and feature toggle state.

## Service Tiers

| Tier | Notes |
|------|-------|
| **Free** | Basic functionality; customer-managed keys NOT supported |
| **Standard** | Full feature set, including customer-managed key encryption |

## Core Features

| Feature | Description |
|---------|-------------|
| Key-value store | Configuration data as case-sensitive, unicode key-value pairs |
| Labels | Differentiate key-values per environment or version |
| Feature flags | Centralized repository for feature toggles |
| Point-in-time replay | Review or restore settings at a past point in time |
| Encryption | At rest (AES-256) and in transit (TLS) |
| Managed identities | System-assigned and user-assigned identities supported |
| Private endpoints | VNet-level access, eliminating public internet exposure |

## Key-Value Data Model

- Keys are **case-sensitive**, **unicode-based** strings.
- Hierarchical keys recommended (using `:` or `/` delimiter).
- Reserved characters: `*`, `,`, `\` — must be escaped.
- Size limit: 10,000 characters per key-value pair.
- Labels differentiate the same key across environments (Test / Staging / Production).
- No automatic versioning — use labels for version management.

## Feature Flag Support

Azure App Configuration is the recommended **centralized repository** for [[feature-flags]]. Feature flags stored externally can be toggled without redeployment.

## Security

- Default encryption: 256-bit AES, Microsoft-managed.
- Customer-managed keys: requires Standard tier, Azure Key Vault (soft-delete + purge-protection), and a managed identity with `GET`/`WRAP`/`UNWRAP` permissions.
- Private endpoints: network traffic stays on Microsoft backbone network.

## CLI Commands

```bash
# Add system-assigned identity
az appconfig identity assign --name myTestAppConfigStore --resource-group myResourceGroup

# Create user-assigned identity and assign
az identity create --resource-group myResourceGroup --name myUserAssignedIdentity
az appconfig identity assign --name myTestAppConfigStore --resource-group myResourceGroup \
    --identities /subscriptions/.../myUserAssignedIdentity
```

## Boundary with Key Vault

> "App Configuration isn't a replacement solution for Azure Key Vault. Don't store application secrets in it."

## Related Pages

- [[azure-key-vault]] – complementary secrets store
- [[managed-identity]] – used for customer-managed key integration
- [[microsoft-entra-id]] – identity platform
- [[feature-flags]] – feature toggle concept
- [[explore-app-configuration]] – service overview source
- [[app-configuration-keys-values]] – key-value data model source
- [[app-configuration-feature-management]] – feature management source
- [[secure-app-configuration-data]] – encryption and private endpoints source
