---
title: "Implement Authentication and Authorization in Azure Container Apps"
type: source
tags: [container-apps, aca, authentication, authorization, federated-identity, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_5-container-apps-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Implement Authentication and Authorization in Azure Container Apps

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_5-container-apps-authentication.pdf

## Overview

[[azure-container-apps]] provides **built-in authentication and authorization** (EasyAuth-style) with minimal or no code, using federated identity providers.

## Key Claims

- Built-in auth requires no specific language, SDK, or security expertise.
- Feature should only be used with **HTTPS** — ensure `allowInsecure` is disabled.
- Auth module runs as a **sidecar container** on each replica, isolated from application code.
- Relevant identity info is injected into **HTTP request headers**.

## Access Modes

| Mode | Configuration |
|---|---|
| Authenticated users only | Set *Restrict access* to **Require authentication** |
| Authenticate but allow unauthenticated | Set *Restrict access* to **Allow unauthenticated access** |

## Identity Providers

| Provider | Sign-in endpoint |
|---|---|
| Microsoft Identity Platform | `/.auth/login/aad` |
| Facebook | `/.auth/login/facebook` |
| GitHub | `/.auth/login/github` |
| Google | `/.auth/login/google` |
| X (Twitter) | `/.auth/login/twitter` |
| Any OpenID Connect provider | `/.auth/login/<providerName>` |

## Middleware Responsibilities

The auth middleware (sidecar):
- Authenticates users and clients with specified identity providers
- Manages the authenticated session
- Injects identity information into HTTP request headers

## Authentication Flows

| Flow | Description |
|---|---|
| **Server-directed** (without provider SDK) | App delegates federated sign-in to Container Apps. Typical for browser apps. |
| **Client-directed** (with provider SDK) | App signs users in manually and submits the token to Container Apps for validation. Typical for native mobile apps. |

## Related Pages

- [[azure-container-apps]] – entity page
- [[federated-identity]] – concept page
- [[sidecar-pattern]] – concept page
- [[aca-explore]] – ACA overview source
- [[aca-revisions-secrets]] – revisions and secrets source
