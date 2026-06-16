---
title: "Microsoft Graph"
type: entity
tags: [microsoft-graph, microsoft-365, rest-api, sdk, az204]
sources: [learn.microsoft.com_en-us_training_modules_microsoft-graph_2-microsoft-graph-overview.pdf,
          learn.microsoft.com_en-us_training_modules_microsoft-graph_3-microsoft-graph-api.pdf,
          learn.microsoft.com_en-us_training_modules_microsoft-graph_4-microsoft-graph-sdk.pdf,
          learn.microsoft.com_en-us_training_modules_microsoft-graph_5-microsoft-graph-best-practices.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Graph

## What It Is

Microsoft Graph is a **unified REST API** and the gateway to data and intelligence in Microsoft 365. It provides a single endpoint (`https://graph.microsoft.com`) for accessing data across Microsoft 365, Windows 10, and Enterprise Mobility + Security.

## Three Platform Components

| Component | Direction | Description |
|-----------|-----------|-------------|
| **Microsoft Graph API** | Outbound (app → MS data) | Single REST endpoint; REST APIs + SDKs |
| **Microsoft Graph connectors** | Inbound (external → MS) | Brings external data (Box, Google Drive, Jira, Salesforce) into Microsoft Graph |
| **Microsoft Graph Data Connect** | Outbound (MS data → Azure) | Delivers Graph data to Azure data stores at scale |

## API Versions

| Version | Use |
|---------|-----|
| `v1.0` | Production apps — generally available APIs |
| `beta` | Development/testing only — may break |

## .NET SDK Packages

| Package | Description |
|---------|-------------|
| `Microsoft.Graph` | Models and request builders for `v1.0` |
| `Microsoft.Graph.Beta` | Models and request builders for `beta` |
| `Microsoft.Graph.Core` | Core library with retry, redirect, auth, compression, paging, batching |

## Key Best Practices

- Use **MSAL** to acquire OAuth 2.0 access tokens.
- Use **least privilege** permissions.
- Handle **pagination** via `@odata.nextLink`.
- Use **delegated permissions** for interactive apps; **application permissions** for daemons.
- Prefer **real-time calls** over local data storage.

## Related Pages

- [[microsoft-identity-platform]] – authentication gateway for Graph
- [[msal]] – used to acquire tokens for Graph
- [[permissions-and-consent]] – scopes govern Graph access
- [[microsoft-graph-rest-api]] – REST querying source
- [[microsoft-graph-sdk]] – SDK usage source
- [[microsoft-graph-best-practices]] – best practices source

## Source References

- [[microsoft-graph-overview]]
- [[microsoft-graph-rest-api]]
- [[microsoft-graph-sdk]]
- [[microsoft-graph-best-practices]]
