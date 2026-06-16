---
title: "MSAL (Microsoft Authentication Library)"
type: entity
tags: [msal, authentication, sdk, token, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_2-microsoft-authentication-library-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_3-initialize-client-applications.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# MSAL (Microsoft Authentication Library)

## What It Is

MSAL is an open-source library that enables developers to acquire security tokens from the [[microsoft-identity-platform]] to authenticate users and access secured web APIs. It is the recommended library for integrating with the Microsoft identity platform.

## Capabilities

- Acquires tokens on behalf of a user or an application.
- Maintains a **token cache** and handles token refresh automatically.
- Supports multiple **authentication flows** and many platforms.
- Provides logging, telemetry, and exception handling.
- Abstracts OAuth 2.0 protocol details.

## Client Application Types

| Type | Description | Can Hold Secrets? |
|------|-------------|------------------|
| **Public client** | Desktop, mobile, browser apps | No — secrets are not safe |
| **Confidential client** | Web apps, web APIs, daemons | Yes — secrets passed in back channel only |

## Supported Authentication Flows

| Flow | Recommended Use |
|------|----------------|
| Authorization code + PKCE | SPA, web, desktop, mobile |
| Client credentials | Daemon / service-to-service |
| Device code | IoT, CLI |
| On-behalf-of (OBO) | Web API → downstream API |
| IWA | Domain-joined desktops |
| Implicit grant | Deprecated; use auth code + PKCE |
| ROPC | Not recommended |

## MSAL.NET Initialization

Use `PublicClientApplicationBuilder` or `ConfidentialClientApplicationBuilder` with `.With*` modifiers. See [[msal-client-initialization]].

## Related Pages

- [[microsoft-identity-platform]] – the platform MSAL targets
- [[msal-overview]] – MSAL overview source page
- [[msal-client-initialization]] – initialization source page
- [[permissions-and-consent]] – scopes requested via MSAL
- [[microsoft-graph]] – common API accessed using MSAL tokens

## Source References

- [[msal-overview]]
- [[msal-client-initialization]]
