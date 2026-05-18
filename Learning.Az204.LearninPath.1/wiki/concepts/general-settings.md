---
title: "General Settings"
type: concept
tags: [configuration, platform, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_3-configure-general-settings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# General Settings

## Definition

**General settings** control the runtime stack, platform behaviour, and debugging options for an [[azure-app-service]] app. Found at **Configuration → General settings** in the Azure portal.

## Categories

### Stack Settings
- Language and SDK version.
- Optional startup command (Linux / custom containers).

### Platform Settings

| Setting | Purpose |
|---------|---------|
| Platform bitness | 32-bit or 64-bit (Windows only) |
| FTP state | FTPS only or disabled |
| HTTP version | Opt into HTTP/2 |
| Web sockets | Enable WebSocket protocol |
| Always On | Keep app loaded; prevents 20-min idle unload |
| ARR Affinity | Route client to same VM instance (session stickiness) |
| HTTPS Only | Force redirect HTTP → HTTPS |
| Minimum TLS version | Enforce a minimum TLS version |
| Debugging | Enable remote debugging (auto-disables) |

### Always On

Required for:
- Continuous WebJobs
- CRON-triggered WebJobs

Without Always On, the app is unloaded after 20 minutes of inactivity, causing high cold-start latency.

## Related Pages

- [[configure-general-settings]] – source page
- [[application-settings]] – app-specific environment variables
- [[azure-app-service]] – the platform
- [[app-service-plan]] – some settings require higher pricing tiers
