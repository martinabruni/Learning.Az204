---
title: "OAuth 2.0 and OpenID Connect"
type: concept
tags: [oauth2, openid-connect, protocol, authorization, authentication, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# OAuth 2.0 and OpenID Connect

## What They Are

- **OAuth 2.0** — an industry-standard authorization protocol that allows third-party apps to access web-hosted resources on behalf of a user. The [[microsoft-identity-platform]] implements this protocol.
- **OpenID Connect (OIDC)** — an authentication layer built on top of OAuth 2.0; used for user sign-in and identity verification.

## Role in the Microsoft Identity Platform

The Microsoft identity platform is **OAuth 2.0 and OpenID Connect standard-compliant**. It implements:
- Human-readable **scopes** (permissions) as string values.
- Authorization flows via the `https://login.microsoftonline.com/common/oauth2/v2.0/authorize` endpoint.
- Token issuance and refresh via the token endpoint.

## Key Concepts

| Concept | Description |
|---------|-------------|
| Scope | A string identifying a permission (e.g., `https://graph.microsoft.com/User.Read`) |
| Access token | Short-lived token proving authorization to access a resource |
| Authorization code | Short-lived code exchanged for tokens (used in the auth code flow) |
| Redirect URI | Where the identity provider sends tokens/codes after authentication |
| Authority | Identity provider URL + tenant/audience (e.g., `https://login.microsoftonline.com/{tenant}`) |

## Related Pages

- [[microsoft-identity-platform]] – the platform implementing these protocols
- [[permissions-and-consent]] – scopes and consent in OAuth 2.0
- [[msal]] – MSAL abstracts OAuth 2.0 implementation
- [[microsoft-graph]] – a resource accessed using OAuth 2.0 tokens
