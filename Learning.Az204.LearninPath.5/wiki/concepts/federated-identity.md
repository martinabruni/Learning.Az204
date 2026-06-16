---
title: "Federated Identity (Container Apps EasyAuth)"
type: concept
tags: [container-apps, aca, authentication, federated-identity, easyauth, az204]
sources: [aca-authentication.md]
created: 2026-06-16
updated: 2026-06-16
---

# Federated Identity in Azure Container Apps

Federated identity in [[azure-container-apps]] is the pattern where a **third-party identity provider manages user identities and authentication flow**. ACA's built-in auth feature (similar to App Service EasyAuth) implements this pattern.

## How It Works

- The auth and authorization middleware runs as a **sidecar container** on each replica.
- Every incoming HTTP request passes through the security layer before reaching the application.
- The module is isolated from application code — no SDK or language integration required.
- Identity information is injected into **HTTP request headers**.

## Supported Identity Providers

| Provider | Endpoint |
|---|---|
| Microsoft Identity Platform | `/.auth/login/aad` |
| Facebook | `/.auth/login/facebook` |
| GitHub | `/.auth/login/github` |
| Google | `/.auth/login/google` |
| X (Twitter) | `/.auth/login/twitter` |
| Any OpenID Connect | `/.auth/login/<providerName>` |

## Authentication Flows

- **Server-directed (server flow)**: App delegates sign-in to Container Apps; typical for browser apps.
- **Client-directed (client flow)**: App signs users in using the provider SDK and submits the token; typical for native mobile apps.

## Configuration

- Require HTTPS (`allowInsecure` = disabled).
- Access modes: *Require authentication* or *Allow unauthenticated access*.

## Related Pages

- [[azure-container-apps]] – entity page
- [[aca-authentication]] – source page
- [[sidecar-pattern]] – the architectural pattern used
