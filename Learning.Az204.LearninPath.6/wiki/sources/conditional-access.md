---
title: "Discover Conditional Access"
type: source
tags: [conditional-access, entra-id, mfa, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Conditional Access

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf

## Overview

[[conditional-access]] is a feature in [[microsoft-entra-id]] that secures apps and services. It is applied via policies that developers and enterprise customers configure.

## Key Claims

### What Conditional Access Enables

- **Multifactor authentication (MFA)**
- Allowing only **Intune enrolled devices** to access specific services
- **Restricting user locations and IP ranges**

### Impact on Applications

- In most cases, Conditional Access does **not change** an app's behavior or require developer code changes.
- Code changes are required only when an app **indirectly or silently requests a token** for a service.

### Scenarios Requiring Code Changes

- Apps performing the **on-behalf-of flow**
- Apps accessing **multiple services/resources**
- **Single-page apps** using MSAL.js
- **Web apps calling a resource**

### Challenge Handling

- Conditional Access policies can be applied or removed at any time by enterprise customers.
- Apps must implement **challenge handling** to continue functioning when a new policy is applied.

### Concrete Examples

1. A single-tenant iOS app signs in a user with no API access — policy is automatically invoked, MFA triggered transparently.
2. An app using a **middle tier service** to access a downstream API: when a policy is applied to the downstream API, the middle tier receives a claims "challenge" and must propagate it back to the app.

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf
> "For your app to continue functioning when a new policy is applied, implement challenge handling."

## Related Pages

- [[microsoft-identity-platform]] – platform overview
- [[microsoft-entra-id]] – identity provider hosting CA policies
- [[conditional-access]] – concept page
- [[msal]] – handles CA challenges in token acquisition
