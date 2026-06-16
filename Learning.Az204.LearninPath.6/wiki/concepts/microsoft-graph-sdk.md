---
title: "Microsoft Graph SDK"
type: concept
tags: [microsoft-graph, sdk, dotnet, fluent-api, az204]
sources: [learn.microsoft.com_en-us_training_modules_microsoft-graph_4-microsoft-graph-sdk.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Graph SDK

## What It Is

The Microsoft Graph SDKs are client libraries designed to simplify building high-quality, efficient, and resilient applications that access [[microsoft-graph]]. They include two components:

1. **Service library** — models and request builders generated from Microsoft Graph metadata; provides discoverable, type-safe API surface.
2. **Core library** — retry handling, secure redirects, transparent authentication, payload compression, paging, and batch requests.

## .NET SDK Architecture

| Package | Endpoint | Description |
|---------|----------|-------------|
| `Microsoft.Graph` | v1.0 | Models + request builders; depends on `Microsoft.Graph.Core` |
| `Microsoft.Graph.Beta` | beta | Models + request builders; depends on `Microsoft.Graph.Core` |
| `Microsoft.Graph.Core` | Both | Core features; shared dependency |

## Key Patterns

- **Single `GraphServiceClient` instance** per application lifetime.
- Authentication is injected via an authentication provider (e.g., MSAL `DeviceCodeCredential`).
- CRUD operations map to: `.GetAsync()`, `.PostAsync()`, `.PatchAsync()`, `.DeleteAsync()`.
- List queries support `$filter`, `$select`, `$orderBy` query parameters via fluent request configuration.

## Related Pages

- [[microsoft-graph]] – entity page
- [[msal]] – provides authentication tokens for the SDK client
- [[microsoft-graph-rest-api]] – REST alternative to SDK
- [[microsoft-graph-best-practices]] – best practices applicable to SDK usage
- [[microsoft-graph-sdk]] – source page
