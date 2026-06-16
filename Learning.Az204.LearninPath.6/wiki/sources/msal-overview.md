---
title: "Explore the Microsoft Authentication Library (MSAL)"
type: source
tags: [msal, authentication, token, sdk, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_2-microsoft-authentication-library-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore the Microsoft Authentication Library (MSAL)

> [!source] learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_2-microsoft-authentication-library-overview.pdf

## Overview

[[msal]] (Microsoft Authentication Library) enables developers to acquire security tokens from the [[microsoft-identity-platform]] to authenticate users and access secured web APIs.

> [!source] learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_2-microsoft-authentication-library-overview.pdf
> "MSAL gives you many ways to get tokens, with a consistent API for many platforms."

## Key Claims

### Benefits of MSAL

- No need to directly use OAuth libraries or code against the protocol.
- Acquires tokens on behalf of a user or application.
- Maintains a **token cache** and refreshes tokens automatically when close to expiry.
- Helps specify the sign-in audience.
- Supports configuration from files.
- Exposes actionable exceptions, logging, and telemetry for troubleshooting.

### Supported Platforms

| Library | Supported platforms |
|---------|---------------------|
| MSAL for Android | Android |
| MSAL Angular | Angular, Angular.js |
| MSAL for iOS and macOS | iOS, macOS |
| MSAL Go (Preview) | Windows, macOS, Linux |
| MSAL Java | Windows, macOS, Linux |
| MSAL.js | Vue.js, Ember.js, Durandal.js |
| MSAL.NET | .NET Framework, .NET, .NET MAUI, WinUI, Xamarin Android, Xamarin iOS, UWP |
| MSAL Node | Express, Electron, cross-platform console |
| MSAL Python | Windows, macOS, Linux |
| MSAL React | React, Next.js, Gatsby.js |

### Authentication Flows

| Flow | Enables | App Types |
|------|---------|-----------|
| Authorization code | User sign-in, API access on behalf of user | Desktop, Mobile, SPA (PKCE required), Web |
| Client credentials | API access using app identity (no user) | Daemon |
| Device code | Sign-in on input-constrained devices (IoT, CLI) | Desktop, Mobile |
| Implicit grant | User sign-in (deprecated — use auth code + PKCE) | SPA, Web |
| On-behalf-of (OBO) | Upstream API → downstream API on behalf of user | Web API |
| Username/password (ROPC) | Direct password handling (NOT recommended) | Desktop, Mobile |
| Integrated Windows auth (IWA) | Silent token acquisition on domain-joined machines | Desktop, Mobile |

### Public vs Confidential Clients

- **Public client applications** — run on devices (desktop, mobile, browser); cannot hold secrets safely; support only public client flows.
- **Confidential client applications** — run on servers (web apps, APIs, daemons); can hold secrets or certificates; client secret passed only in back channel.

## Related Pages

- [[msal]] – entity/concept page
- [[microsoft-identity-platform]] – the platform MSAL targets
- [[msal-client-initialization]] – how to initialize MSAL clients
- [[oauth2-and-openid-connect]] – underlying protocols
