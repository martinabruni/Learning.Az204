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

## [2026-06-16] ingest | AZ-204 Learning Path 6 — Microsoft Identity, MSAL, SAS, Microsoft Graph (13 PDFs)

**Raw sources processed:** 13 PDFs across 4 Microsoft Learn modules.

**Modules ingested:**
1. `explore-microsoft-identity-platform` (4 units: overview, service principals, permissions/consent, conditional access)
2. `implement-authentication-by-using-microsoft-authentication-library` (2 units: MSAL overview, client initialization)
3. `implement-shared-access-signatures` (3 units: SAS overview, when to use SAS, stored access policies)
4. `microsoft-graph` (4 units: overview, REST API, SDK, best practices)

**Files Added:**

*Sources (13):*
- `sources/microsoft-identity-platform-overview.md`
- `sources/explore-service-principals.md`
- `sources/permissions-and-consent.md`
- `sources/conditional-access.md`
- `sources/msal-overview.md`
- `sources/msal-client-initialization.md`
- `sources/sas-overview.md`
- `sources/sas-use-cases.md`
- `sources/stored-access-policies.md`
- `sources/microsoft-graph-overview.md`
- `sources/microsoft-graph-rest-api.md`
- `sources/microsoft-graph-sdk.md`
- `sources/microsoft-graph-best-practices.md`

*Entities (4):*
- `entities/microsoft-identity-platform.md`
- `entities/microsoft-entra-id.md`
- `entities/msal.md`
- `entities/microsoft-graph.md`

*Concepts (8):*
- `concepts/service-principals.md`
- `concepts/managed-identity.md`
- `concepts/permissions-and-consent.md`
- `concepts/conditional-access.md`
- `concepts/oauth2-and-openid-connect.md`
- `concepts/shared-access-signature.md`
- `concepts/stored-access-policies.md`
- `concepts/microsoft-graph-sdk.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Microsoft Identity Platform** is OAuth 2.0 and OpenID Connect compliant; supports work/school accounts (Entra ID), personal Microsoft accounts, Azure AD B2C accounts, and Entra External ID customer accounts.
- **Application object** (global, home tenant) serves as a template; **service principal** (local, per tenant) is the runtime identity. App object has 1-to-many relationship with service principals.
- Three types of service principal: Application, Managed identity (cannot be modified directly), Legacy (no app registration).
- **Permissions** are OAuth 2.0 scopes — string values like `https://graph.microsoft.com/User.Read`. Two types: delegated (user present) and app-only (no user; admin consent required).
- Three consent types: static (all permissions declared upfront), dynamic/incremental (scopes added progressively), admin (for high-privilege operations; org-wide).
- **Conditional Access** generally requires no code changes; code changes needed for OBO flows, multi-service apps, SPAs, and web apps calling resources with CA policies.
- **MSAL** abstracts OAuth 2.0 protocol; supports 10+ platform libraries; manages token cache and refresh automatically. Two client types: public (devices, no secrets) and confidential (servers, can hold secrets).
- **MSAL.NET 3.x**: uses builder pattern (`PublicClientApplicationBuilder` / `ConfidentialClientApplicationBuilder`). `.WithCertificate()` and `.WithClientSecret()` are mutually exclusive.
- **SAS**: signed URI granting limited storage access. Three types: user delegation (Entra — most secure), service (account key, single service), account (account key, all services). Best practice: use user delegation SAS, HTTPS, minimum expiry, minimum privileges.
- **Stored access policies** enable server-side revocation of service-level SAS. Take up to 30 seconds to take effect. Deleting or changing the signed identifier immediately revokes all associated SAS.
- **Microsoft Graph**: single endpoint `https://graph.microsoft.com`; three platform components: Graph API (outbound), Connectors (inbound), Data Connect (Graph → Azure data stores). Two versions: v1.0 (production) and beta (dev only).
- **Graph SDK .NET**: two NuGet packages per version (`Microsoft.Graph`/`Microsoft.Graph.Beta`) plus `Microsoft.Graph.Core`. Single `GraphServiceClient` instance per app lifetime; authentication via MSAL provider.
- **Graph best practices**: use MSAL for token acquisition; least privilege; correct permission type (delegated vs application); handle pagination via `@odata.nextLink`; handle evolvable enumerations; prefer real-time calls over local data storage.

**Contradictions found:** None detected across the 13 source documents. The requirement to use Entra credentials (user delegation SAS) is consistently recommended over storage account keys across both SAS modules. MSAL is consistently recommended for token acquisition in both the identity platform and Microsoft Graph modules.
