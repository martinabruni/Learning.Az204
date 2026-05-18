---
title: "Configure General Settings"
type: source
tags: [app-service, configuration, platform, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_3-configure-general-settings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Configure General Settings

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_3-configure-general-settings.pdf

## Overview

The **Configuration → General settings** blade exposes common runtime and platform options for [[azure-app-service]]. Some settings require scaling up to higher [[app-service-plan]] tiers.

## Stack Settings

- Runtime language and SDK version.
- For Linux / custom containers: optional startup command or file.

## Platform Settings

| Setting | Detail |
|---------|--------|
| Platform bitness | 32-bit or 64-bit (Windows only) |
| FTP state | FTPS only or fully disabled |
| HTTP version | 2.0 enables HTTP/2 over TLS |
| Web sockets | Required for SignalR / socket.io |
| Always On | Prevents app unload after 20 min of inactivity |
| ARR Affinity | Pins client session to same VM instance |
| HTTPS Only | Redirects all HTTP to HTTPS |
| Minimum TLS version | Minimum encryption version required |
| Debugging | Remote debug for ASP.NET/Node.js (auto-off) |

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_3-configure-general-settings.pdf
> "When Always On is turned on, the front-end load balancer sends a GET request to the application root every five minutes."

### Always On Requirement

Always On is **required** for continuous WebJobs or CRON-triggered WebJobs.

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_3-configure-general-settings.pdf
> "Most modern browsers support HTTP/2 protocol over TLS only, while non-encrypted traffic continues to use HTTP/1.1."

## Related Pages

- [[general-settings]] – concept page
- [[configure-web-app-settings-introduction]] – module intro
- [[app-service-plan]] – pricing tier affects available settings
