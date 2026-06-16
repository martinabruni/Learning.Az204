---
title: "Permissions and Consent"
type: concept
tags: [oauth2, permissions, scopes, consent, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Permissions and Consent

## What It Is

The permissions and consent model of the [[microsoft-identity-platform]] (built on **OAuth 2.0**) gives users and administrators control over how applications access data. Permissions are represented as **scopes** — string values appended to a resource's application ID URI.

## Permission Types

| Type | When Used | Who Consents |
|------|-----------|-------------|
| **Delegated access** | App has a signed-in user | User or admin |
| **App-only access** | No signed-in user (daemon, background service) | Admin only |

## Consent Types

| Type | Description | Drawbacks |
|------|-------------|-----------|
| **Static user consent** | All permissions declared in Azure portal at registration; admin can consent for org | Must know all resources upfront; long permission list on first sign-in |
| **Incremental/dynamic consent** | Request minimum upfront; add scopes incrementally as features are used | Challenges with admin-privileged permissions; register all in portal if needed |
| **Admin consent** | For high-privilege permissions; admin consents on behalf of org; requires static permissions registered | N/A |

## How Apps Request Permissions

Apps include a `scope` query parameter in the authorization request:

```
GET https://login.microsoftonline.com/common/oauth2/v2.0/authorize?
    client_id=...
    &scope=https://graph.microsoft.com/Calendars.Read https://graph.microsoft.com/Mail.Send
    &...
```

- Omitting the resource ID defaults to Microsoft Graph (`scope=User.Read` = `https://graph.microsoft.com/User.Read`).
- Platform checks for existing user consent; prompts if not previously granted.

## Related Pages

- [[microsoft-identity-platform]] – the platform implementing this model
- [[microsoft-entra-id]] – the identity provider enforcing consent
- [[oauth2-and-openid-connect]] – underlying protocol
- [[msal]] – library used to acquire tokens with scopes
- [[microsoft-graph]] – a key resource requiring scope-based permissions
- [[permissions-and-consent]] – source page
