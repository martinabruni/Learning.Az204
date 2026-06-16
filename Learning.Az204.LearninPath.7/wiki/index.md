---
title: "Wiki Index – AZ-204 Learning Path 7: Managed Identities, Key Vault, and App Configuration"
type: synthesis
tags: [index, az204, managed-identity, key-vault, app-configuration]
sources: [explore-managed-identities.md, explore-azure-key-vault.md, explore-app-configuration.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 7: Managed Identities, Key Vault, and App Configuration

This wiki is built from the 11 PDFs in `raw/`, covering three Microsoft Learn modules on Azure security services.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[managed-identity]] | Automatically managed Entra ID service principal for credential-free Azure resource authentication |
| [[azure-key-vault]] | Cloud service for securely storing secrets, keys, and certificates with HSM support |
| [[azure-app-configuration]] | Fully managed service for centralized application settings and feature flag management |
| [[microsoft-entra-id]] | Microsoft's cloud identity platform; authentication backbone for all Azure services in this LP |
| [[azure-resource-manager]] | Azure deployment service that creates and configures managed identity service principals |

---

## Concepts

| Page | Summary |
|------|---------|
| [[default-azure-credential]] | Azure Identity SDK type that chains multiple auth mechanisms; no code changes between dev and prod |
| [[feature-flags]] | Boolean toggles that decouple feature release from code deployment; managed in App Configuration |
| [[key-vault-access-control]] | RBAC and access policy models for Key Vault authentication and authorization |
| [[app-configuration-security]] | Customer-managed keys, private endpoints, and managed identities securing App Configuration |

---

## Sources — Module 1: Implement Managed Identities

| Page | PDF |
|------|-----|
| [[explore-managed-identities]] | `implement-managed-identities_2-managed-identities-overview.pdf` |
| [[managed-identities-authentication-flow]] | `implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf` |
| [[configure-managed-identities]] | `implement-managed-identities_4-configure-managed-identities.pdf` |
| [[acquire-access-token]] | `implement-managed-identities_5-acquire-access-token.pdf` |

## Sources — Module 2: Implement Azure Key Vault

| Page | PDF |
|------|-----|
| [[explore-azure-key-vault]] | `implement-azure-key-vault_2-key-vault-overview.pdf` |
| [[key-vault-best-practices]] | `implement-azure-key-vault_3-key-vault-concepts.pdf` |
| [[key-vault-authentication]] | `implement-azure-key-vault_4-key-vault-authentication.pdf` |

## Sources — Module 3: Implement Azure App Configuration

| Page | PDF |
|------|-----|
| [[explore-app-configuration]] | `implement-azure-app-configuration_2-app-configuration-overview.pdf` |
| [[app-configuration-keys-values]] | `implement-azure-app-configuration_3-keys-values.pdf` |
| [[app-configuration-feature-management]] | `implement-azure-app-configuration_4-app-configuration-feature-management.pdf` |
| [[secure-app-configuration-data]] | `implement-azure-app-configuration_5-secure-app-configuration-data.pdf` |

---

## Page Counts

- Sources: 11
- Entities: 5
- Concepts: 4
- **Total wiki pages: 20** (plus this index and log.md)
