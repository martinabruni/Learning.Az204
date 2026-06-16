---
title: "Discover Permissions and Consent"
type: source
tags: [oauth2, permissions, consent, scopes, entra-id, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Permissions and Consent

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf

## Overview

The [[microsoft-identity-platform]] implements the **OAuth 2.0 authorization protocol**. Applications follow an authorization model giving users and administrators control over how data is accessed.

## Key Claims

### Scopes and Permissions

- Any web-hosted resource integrated with the platform has a **resource identifier** (application ID URI).
- Permissions are called **scopes** in OAuth 2.0 and are represented as string values.
- Apps request permissions via the `scope` query parameter.
- Example: `https://graph.microsoft.com/Calendars.Read` requests permission to read calendars in Microsoft Graph.
- If the resource identifier is omitted, `scope=User.Read` defaults to `https://graph.microsoft.com/User.Read`.

### Microsoft Web-Hosted Resources

| Resource | ID URI |
|----------|--------|
| Microsoft Graph | `https://graph.microsoft.com` |
| Microsoft 365 Mail API | `https://outlook.office.com` |
| Azure Key Vault | `https://vault.azure.net` |

### Permission Types

- **Delegated access** — used when a signed-in user is present; user or admin consents; app acts as the signed-in user.
- **App-only access** — used by background services/daemons with no signed-in user; only admins can consent.

### Consent Types

1. **Static user consent** — all permissions declared upfront in Azure portal; enables admin consent for whole org; risks: long permission list on first sign-in, must know all resources ahead of time.
2. **Incremental and dynamic user consent** — request minimum permissions upfront, add more over time via `scope` parameter in access token requests; only applies to delegated permissions (not app-only).
3. **Admin consent** — required for high-privilege permissions; admin consents on behalf of the organization; static permissions must still be registered in portal when dynamic consent is also used.

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf
> "Dynamic consent can be convenient, but presents a big challenge for permissions that require admin consent, since the admin consent experience doesn't know about those permissions at consent time."

### Requesting Individual User Consent

- App sends a GET to the authorization endpoint with `scope` containing space-separated permission strings.
- Example endpoint: `https://login.microsoftonline.com/common/oauth2/v2.0/authorize`
- Platform checks for existing user consent record; prompts if not previously granted.

## Related Pages

- [[microsoft-identity-platform]] – the identity platform
- [[permissions-and-consent]] – concept page
- [[oauth2-and-openid-connect]] – underlying protocol
- [[msal]] – library for requesting tokens with scopes
- [[microsoft-graph]] – common resource requiring scope-based access
