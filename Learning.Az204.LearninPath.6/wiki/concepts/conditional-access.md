---
title: "Conditional Access"
type: concept
tags: [conditional-access, entra-id, mfa, security, policy, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_5-conditional-access.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Conditional Access

## What It Is

Conditional Access is a feature of [[microsoft-entra-id]] that enforces access policies to protect apps and services. Policies are applied at the tenant level and can be added or removed at any time by enterprise customers.

## Policy Capabilities

- **Multifactor authentication (MFA)** enforcement
- Allowing only **Intune enrolled devices** to access specific services
- **Restricting user locations and IP ranges**

## Developer Impact

- In most cases, Conditional Access is **transparent** — no code changes required.
- Code changes are needed only when an app **silently or indirectly requests a token** and CA is applied to the target service.

### Scenarios Requiring Code Changes

| Scenario | Why |
|----------|-----|
| On-behalf-of (OBO) flow | Middle tier must propagate claims challenges |
| Apps accessing multiple services/resources | Each resource may have different CA policies |
| SPAs using MSAL.js | Silent token acquisition may be interrupted |
| Web apps calling a resource | Resource may enforce CA after app already signed in |

## Challenge Handling

- When CA denies a silent token request, a **claims challenge** is returned.
- The app must **perform an interactive sign-in** to satisfy the CA policy.
- For OBO scenarios: the middle tier must **send the challenge back to the calling app**.

## Related Pages

- [[microsoft-entra-id]] – the identity provider hosting CA policies
- [[microsoft-identity-platform]] – the platform integrating CA
- [[msal]] – handles CA challenge responses in token acquisition
- [[conditional-access]] – source page
