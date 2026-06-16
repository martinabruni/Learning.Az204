---
title: "Explore the Microsoft Identity Platform"
type: source
tags: [identity-platform, entra-id, msal, oauth2, openid-connect, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore the Microsoft Identity Platform

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf

## Overview

The [[microsoft-identity-platform]] helps developers build applications where users sign in using Microsoft identities or social accounts, and provides authorized access to APIs.

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_2-microsoft-identity-platform-overview.pdf
> "The Microsoft identity platform helps you build applications your users and customers can sign in to using their Microsoft identities or social accounts, and provide authorized access to your own APIs or Microsoft APIs like Microsoft Graph."

## Key Claims

- The platform is **OAuth 2.0 and OpenID Connect standard-compliant**.
- Supports multiple identity types: work/school accounts (Entra ID), personal Microsoft accounts (Xbox, Outlook.com), social/local accounts (Azure AD B2C), customer accounts (Entra External ID).
- Includes open-source libraries: [[msal|Microsoft Authentication Libraries (MSAL)]] and other standards-compliant libraries.
- Provides a **Microsoft identity platform endpoint** that implements human-readable scopes.
- Offers an **Application management portal** in the Azure portal for registration and configuration.
- Supports **programmatic configuration** via Microsoft Graph API and PowerShell (DevOps automation).
- Built-in modern security innovations: passwordless authentication, step-up authentication, [[conditional-access]].

## Data Points

- Unit 2 of 7 in the "Explore the Microsoft identity platform" module.
- Applications integrated with the platform natively take advantage of security innovations — no manual implementation required.

## Related Pages

- [[microsoft-identity-platform]] – entity page
- [[msal]] – open-source authentication library
- [[conditional-access]] – advanced security policy feature
- [[service-principals]] – service principal model
- [[permissions-and-consent]] – OAuth 2.0 scopes and consent
