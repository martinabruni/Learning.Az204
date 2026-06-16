---
title: "Microsoft Entra ID"
type: entity
tags: [entra-id, azure-ad, identity, authentication, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_2-managed-identities-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Entra ID

## What It Is

Microsoft Entra ID (formerly Azure Active Directory) is Microsoft's cloud-based identity and access management service. It is the authentication backbone for Azure resources and services.

## Role in This Learning Path

In Learning Path 7, Microsoft Entra ID appears as the identity provider for:
- [[managed-identity|Managed identities]] — identities are created and managed in an Entra tenant.
- [[azure-key-vault]] — authentication to Key Vault goes through Entra ID.
- [[azure-app-configuration]] — managed identities used by App Configuration are Entra identities.

## Security Principals Authenticated by Entra ID

| Principal Type | Description |
|---------------|-------------|
| **Users** | Real people with Entra ID accounts |
| **Groups** | Collections of users sharing permissions |
| **Service Principals** | App/service identities; managed identities are a special type |

## Token Types

- Issues **JSON Web Token (JWT)** access tokens for authenticated principals.
- Tokens carry scopes and claims that downstream services validate.

## Tenant

A **tenant** is a dedicated instance of Entra ID for an organization. Managed identities are created in the Entra tenant trusted by the Azure subscription.

## Related Pages

- [[managed-identity]] – special service principal managed by Entra ID
- [[azure-key-vault]] – authenticates callers via Entra ID
- [[azure-app-configuration]] – uses Entra ID via managed identities
- [[default-azure-credential]] – SDK type that obtains Entra tokens
