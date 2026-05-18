---
title: "Authentication and Authorization (EasyAuth)"
type: concept
tags: [authentication, authorization, identity, security, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Authentication and Authorization (EasyAuth)

## Definition

**EasyAuth** is the built-in authentication and authorization feature of [[azure-app-service]]. It enables apps to authenticate users with federated identity providers without writing auth code.

## Architecture

- Runs as platform middleware — a **sidecar** process (Windows) or separate container (Linux).
- All HTTP requests pass through EasyAuth before reaching app code.
- Handles token validation, session management, and token refresh.

## Supported Identity Providers

| Provider | Endpoint |
|----------|----------|
| Microsoft Entra ID | `/.auth/login/aad` |
| Facebook | `/.auth/login/facebook` |
| Google | `/.auth/login/google` |
| X (Twitter) | `/.auth/login/x` |
| GitHub | `/.auth/login/github` |
| Apple (preview) | `/.auth/login/apple` |
| Any OpenID Connect | `/.auth/login/<providerName>` |

## Authentication Modes

| Mode | Behaviour |
|------|-----------|
| Allow unauthenticated | App code decides how to handle unauthenticated users |
| Require authentication | Redirects to sign-in page or returns 401/403 |

## Token Store

- Built-in token store at `/.auth/me`.
- Caches and refreshes provider tokens.
- Accessible from app code without extra libraries.

## When to Use EasyAuth

- Minimal code overhead.
- Need federated sign-in quickly.
- Optionally combine with custom middleware for additional logic.

## Related Pages

- [[authentication-authorization-app-service]] – source page
- [[azure-app-service]] – the platform
- [[networking-features]] – access restriction complement
