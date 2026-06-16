---
title: "Wiki Index – AZ-204 Learning Path 6: Microsoft Identity, MSAL, SAS, Microsoft Graph"
type: synthesis
tags: [index, az204, identity, msal, sas, microsoft-graph]
sources: [microsoft-identity-platform-overview.md, explore-service-principals.md, permissions-and-consent.md, conditional-access.md, msal-overview.md, msal-client-initialization.md, sas-overview.md, sas-use-cases.md, stored-access-policies.md, microsoft-graph-overview.md, microsoft-graph-rest-api.md, microsoft-graph-sdk.md, microsoft-graph-best-practices.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 6: Microsoft Identity, MSAL, SAS, Microsoft Graph

This wiki is built from 13 PDFs in `raw/`, covering three Microsoft Learn modules on identity, authentication, shared access signatures, and Microsoft Graph.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[microsoft-identity-platform]] | Cloud identity service implementing OAuth 2.0/OpenID Connect for app authentication |
| [[microsoft-entra-id]] | Azure Active Directory; tenant host for app registrations, service principals, and identity policies |
| [[msal]] | Microsoft Authentication Library — open-source SDK for acquiring tokens from the identity platform |
| [[microsoft-graph]] | Unified REST API gateway to Microsoft 365, Windows 10, and Enterprise Mobility + Security data |

---

## Concepts

| Page | Summary |
|------|---------|
| [[service-principals]] | Local per-tenant representation of a registered app or managed identity |
| [[managed-identity]] | Platform-managed service principal providing credential-free access to Azure resources |
| [[permissions-and-consent]] | OAuth 2.0 scopes and three consent types: static, dynamic/incremental, admin |
| [[conditional-access]] | Entra ID policy enforcing MFA, device compliance, and location restrictions; requires challenge handling in some app scenarios |
| [[oauth2-and-openid-connect]] | Industry-standard authorization and authentication protocols underlying the identity platform |
| [[shared-access-signature]] | Signed URI granting limited, time-bound, delegated access to Azure Storage resources |
| [[stored-access-policies]] | Server-side policy grouping SAS tokens, enabling revocation after issuance |
| [[microsoft-graph-sdk]] | Two-component SDK (service library + core library) simplifying Microsoft Graph access |

---

## Sources — Module 1: Explore the Microsoft Identity Platform

| Page | PDF |
|------|-----|
| [[microsoft-identity-platform-overview]] | `explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf` |
| [[explore-service-principals]] | `explore-microsoft-identity-platform_3-app-service-principals.pdf` |
| [[permissions-and-consent]] | `explore-microsoft-identity-platform_4-permission-consent.pdf` |
| [[conditional-access]] | `explore-microsoft-identity-platform_5-conditional-access.pdf` |

## Sources — Module 2: Implement Authentication Using MSAL

| Page | PDF |
|------|-----|
| [[msal-overview]] | `implement-authentication-by-using-microsoft-authentication-library_2-microsoft-authentication-library-overview.pdf` |
| [[msal-client-initialization]] | `implement-authentication-by-using-microsoft-authentication-library_3-initialize-client-applications.pdf` |

## Sources — Module 3: Implement Shared Access Signatures

| Page | PDF |
|------|-----|
| [[sas-overview]] | `implement-shared-access-signatures_2-shared-access-signatures-overview.pdf` |
| [[sas-use-cases]] | `implement-shared-access-signatures_3-shared-access-signatures.pdf` |
| [[stored-access-policies]] | `implement-shared-access-signatures_4-stored-access-policies.pdf` |

## Sources — Module 4: Microsoft Graph

| Page | PDF |
|------|-----|
| [[microsoft-graph-overview]] | `microsoft-graph_2-microsoft-graph-overview.pdf` |
| [[microsoft-graph-rest-api]] | `microsoft-graph_3-microsoft-graph-api.pdf` |
| [[microsoft-graph-sdk]] | `microsoft-graph_4-microsoft-graph-sdk.pdf` |
| [[microsoft-graph-best-practices]] | `microsoft-graph_5-microsoft-graph-best-practices.pdf` |

---

## Page Counts

- Sources: 13
- Entities: 4
- Concepts: 8
- **Total wiki pages: 25** (plus this index and log.md)
