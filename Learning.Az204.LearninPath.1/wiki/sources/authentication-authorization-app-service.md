---
title: "Authentication and Authorization in App Service"
type: source
tags: [app-service, authentication, authorization, identity, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Authentication and Authorization in App Service

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf

## Overview

[[azure-app-service]] provides built-in [[authentication-authorization|EasyAuth]] — authentication and authorization with minimal code.

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf
> "Azure App Service allows you to integrate various auth capabilities into your web app or API without implementing them yourself."

## Benefits

- No SDK or language dependency — built into the platform.
- Supports federated identity via multiple providers simultaneously.
- Saves implementation time.

## Identity Providers

| Provider | Sign-in Endpoint |
|----------|-----------------|
| Microsoft Entra ID | `/.auth/login/aad` |
| Facebook | `/.auth/login/facebook` |
| Google | `/.auth/login/google` |
| X (Twitter) | `/.auth/login/x` |
| GitHub | `/.auth/login/github` |
| Apple (preview) | `/.auth/login/apple` |
| Any OpenID Connect | `/.auth/login/<providerName>` |

> [!source] learn.microsoft.com_en-us_training_modules_introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf
> "App Service uses federated identity, in which a third-party identity provider manages the user identities and authentication flow for you."

## How It Works

- Auth middleware runs as a sidecar (Windows) or separate container (Linux).
- All HTTP requests pass through middleware before reaching app code.
- Modes:
  - **Allow unauthenticated**: app handles auth logic.
  - **Require authentication**: redirects to sign-in or returns 401/403.

## Token Store

Built-in token store at `/.auth/me` caches tokens for authenticated users.

## Related Pages

- [[authentication-authorization]] – concept page
- [[azure-app-service]] – hosting platform
- [[intro-app-service-introduction]] – module overview
