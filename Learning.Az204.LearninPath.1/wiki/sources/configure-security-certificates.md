---
title: "Configure Security Certificates"
type: source
tags: [app-service, tls, ssl, certificates, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_6-configure-security-certificates.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Configure Security Certificates

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_6-configure-security-certificates.pdf

## Overview

[[azure-app-service]] provides tools to create, upload, or import private and public certificates for securing custom domains.

## Certificate Storage

Certificates are stored in a **deployment unit** bound to the App Service plan's resource group and region (webspace). All apps in the same resource group+region can access the certificate.

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_6-configure-security-certificates.pdf
> "A certificate uploaded into an app is stored in a deployment unit that is bound to the app service plan's resource group and region combination."

## Certificate Options

| Option | Description |
|--------|-------------|
| Free App Service managed certificate | Free, auto-renewed; for custom domain security only |
| App Service certificate | Azure-managed; automated renewal and export |
| Import from Key Vault | For organisations using Azure Key Vault |
| Upload private certificate | Third-party PFX certificates |
| Upload public certificate | Access remote resources from code (not for domain security) |

## Private Certificate Requirements

- Exported as password-protected **PFX**, encrypted with triple DES.
- Private key at least **2,048 bits**.
- Full certificate chain (all intermediates + root).
- For TLS binding: Extended Key Usage for server authentication (OID = 1.3.6.1.5.5.7.3.1).

## Related Pages

- [[security-certificates]] – concept page
- [[configure-web-app-settings-introduction]] – module intro
- [[azure-app-service]] – hosting platform
