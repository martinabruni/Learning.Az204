---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204]
sources: [index.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2026-06-16] ingest | AZ-204 Learning Path 7 — Managed Identities, Key Vault, and App Configuration (11 PDFs)

**Raw sources processed:** 11 PDFs across 3 Microsoft Learn modules.

**Modules ingested:**
1. `implement-managed-identities` (4 units: overview, authentication flow, configure, acquire token)
2. `implement-azure-key-vault` (3 units: overview, best practices, authentication)
3. `implement-azure-app-configuration` (4 units: overview, keys-values, feature management, secure data)

**Files Added:**

*Sources (11):*
- `sources/explore-managed-identities.md`
- `sources/managed-identities-authentication-flow.md`
- `sources/configure-managed-identities.md`
- `sources/acquire-access-token.md`
- `sources/explore-azure-key-vault.md`
- `sources/key-vault-best-practices.md`
- `sources/key-vault-authentication.md`
- `sources/explore-app-configuration.md`
- `sources/app-configuration-keys-values.md`
- `sources/app-configuration-feature-management.md`
- `sources/secure-app-configuration-data.md`

*Entities (5):*
- `entities/managed-identity.md`
- `entities/azure-key-vault.md`
- `entities/azure-app-configuration.md`
- `entities/microsoft-entra-id.md`
- `entities/azure-resource-manager.md`

*Concepts (4):*
- `concepts/default-azure-credential.md`
- `concepts/feature-flags.md`
- `concepts/key-vault-access-control.md`
- `concepts/app-configuration-security.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Managed identities** eliminate credential management for service-to-service authentication; they are special-purpose service principals backed by Microsoft Entra ID. Two types: system-assigned (lifecycle tied to resource) and user-assigned (independent, shareable).
- The **Azure Instance Metadata Service (IMDS)** endpoint (`http://169.254.169.254/metadata/identity/oauth2/token`) is the token acquisition point from within a VM — accessible only from inside the VM.
- **DefaultAzureCredential** from the Azure Identity library supports the same code path for both development (CLI/VS auth) and production (managed identity), with no code changes required at deploy time.
- **ChainedTokenCredential** enables custom ordered credential chains for advanced scenarios.
- **Azure Key Vault** supports two container types (vaults and managed HSM pools) and two tiers (Standard / software keys; Premium / HSM-backed keys). Recommended auth: managed identity. Best practice: one vault per app per environment.
- Key Vault enforces **TLS** with **Perfect Forward Secrecy (PFS)** and **RSA-2048** for data in transit. Soft-delete and purge-protection should be enabled.
- Key Vault authorization uses **Azure RBAC** (management + data) or **access policies** (data only).
- **Azure App Configuration** stores settings and feature flags as **case-sensitive, unicode key-value pairs** with optional labels. It is NOT a replacement for Key Vault — do not store secrets in it.
- Labels in App Configuration differentiate the same key across environments (Test / Staging / Production) and serve as a versioning strategy.
- **Feature flags** decouple feature release from code deployment. App Configuration is the recommended centralized feature flag repository.
- App Configuration supports **customer-managed key encryption** (Standard tier only) by wrapping its AES-256 key using a managed identity that calls Key Vault. The unwrapped key is cached for 1 hour.
- **Private endpoints** for App Configuration route traffic over the Microsoft backbone network, eliminating public internet exposure.

**Contradictions found:** None detected. The Managed Identities module and the App Configuration security unit consistently recommend managed identities as the best practice for authenticating to Key Vault, and both modules use the same Azure Identity library (`DefaultAzureCredential`) for code-level authentication. The distinction between App Configuration (config/flags) and Key Vault (secrets) is stated consistently in both the App Configuration overview and the keys-values units.
