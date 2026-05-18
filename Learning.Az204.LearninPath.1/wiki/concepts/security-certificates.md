---
title: "Security Certificates"
type: concept
tags: [tls, ssl, certificates, security, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_6-configure-security-certificates.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Security Certificates

## Definition

**Security certificates** in [[azure-app-service]] are used to secure custom domains via TLS/SSL bindings or to enable code to access remote resources using client certificates.

## Certificate Storage

Stored in a **deployment unit** (webspace) scoped to the resource group + region combination of the [[app-service-plan]]. All apps in the same webspace can access a given certificate.

## Certificate Options

| Option | Use Case | Cost |
|--------|----------|------|
| Free managed certificate | Secure a custom domain | Free |
| App Service certificate | Azure-managed, auto-renewed | Paid |
| Import from Key Vault | Centralised certificate management | Key Vault costs |
| Upload private certificate (PFX) | Third-party certificates | Bring your own |
| Upload public certificate | Code needs to access remote resource | Bring your own |

## Private Certificate Requirements

- Password-protected **PFX**, triple DES encrypted.
- Private key ≥ **2,048 bits**.
- Full certificate chain (all intermediates + root).
- For TLS custom domain binding: Extended Key Usage for server auth (OID = 1.3.6.1.5.5.7.3.1).

## Related Pages

- [[configure-security-certificates]] – source page
- [[azure-app-service]] – the platform
- [[general-settings]] – HTTPS Only and minimum TLS version settings
