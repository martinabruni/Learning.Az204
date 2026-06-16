---
title: "Microsoft Entra ID"
type: entity
tags: [entra-id, azure-ad, identity, tenant, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf,
          learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Entra ID

## What It Is

Microsoft Entra ID (formerly Azure Active Directory) is Microsoft's cloud-based identity and access management service. It serves as the tenant host for application registrations, service principals, and identity policies.

## Key Functions in AZ-204

- **App registration** — registers applications and creates application objects and service principals.
- **Tenant-based access control** — each tenant has its own service principals and consent grants.
- **Conditional Access** — enforces policies such as MFA, device compliance, and IP restrictions.
- **Managed Identities** — provides identities for Azure resources to authenticate to Entra-protected services.

## Tenant Concepts

- **Home tenant** — the tenant where an application object is registered.
- **Single-tenant app** — only one service principal, in the home tenant.
- **Multi-tenant app** — a service principal is created in each tenant where a user consents.

## Related Pages

- [[microsoft-identity-platform]] – the platform built on Entra ID
- [[service-principals]] – service principal model within Entra ID
- [[managed-identity]] – managed identity feature
- [[conditional-access]] – policy enforcement feature in Entra ID
- [[permissions-and-consent]] – authorization model
- [[shared-access-signature]] – user delegation SAS secured with Entra credentials

## Source References

- [[explore-service-principals]]
- [[conditional-access]]
