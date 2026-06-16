---
title: "Microsoft Identity Platform"
type: entity
tags: [identity-platform, entra-id, oauth2, openid-connect, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_4-permission-consent.pdf,
          learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Identity Platform

## What It Is

The Microsoft identity platform is a cloud identity service that helps developers build applications where users sign in with Microsoft identities or social accounts. It provides OAuth 2.0 and OpenID Connect compliant authentication and authorized access to APIs.

## Core Components

| Component | Description |
|-----------|-------------|
| Authentication service | OAuth 2.0 / OpenID Connect compliant; supports work/school, personal, B2C, and External ID accounts |
| MSAL (open-source) | [[msal\|Microsoft Authentication Libraries]] for .NET, JS, Java, Python, Android, iOS |
| Platform endpoint | Implements human-readable scopes; works with MSAL or any standards-compliant library |
| Application management portal | Azure portal app registration and configuration |
| Configuration API/PowerShell | Programmatic configuration via Microsoft Graph API and PowerShell |

## Supported Identity Types

- Work or school accounts (provisioned through [[microsoft-entra-id]])
- Personal Microsoft accounts (Xbox, Outlook.com)
- Social or local accounts (Azure Active Directory B2C)
- Social or local customer accounts (Microsoft Entra External ID)

## Modern Security Features

- Passwordless authentication
- Step-up authentication
- [[conditional-access]] (MFA, device compliance, location restrictions)

## Related Pages

- [[microsoft-entra-id]] – the underlying directory and identity provider
- [[msal]] – open-source authentication library
- [[service-principals]] – app registration and identity model
- [[permissions-and-consent]] – OAuth 2.0 scopes and consent model
- [[conditional-access]] – advanced security policy feature
- [[oauth2-and-openid-connect]] – underlying protocols

## Source References

- [[microsoft-identity-platform-overview]]
- [[permissions-and-consent]]
- [[conditional-access]]
