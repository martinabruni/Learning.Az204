---
title: "Enable Diagnostic Logging"
type: source
tags: [app-service, diagnostics, logging, monitoring, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_5-enable-diagnostic-logging.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Enable Diagnostic Logging

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_5-enable-diagnostic-logging.pdf

## Overview

[[azure-app-service]] provides built-in diagnostics for debugging. This unit covers [[diagnostic-logging]] types, locations, and access methods.

## Log Types

| Type | Platform | Location | Description |
|------|----------|----------|-------------|
| Application logging | Windows, Linux | File system / Azure Storage blobs | App-generated messages; levels: Critical, Error, Warning, Info, Debug, Trace |
| Web server logging | Windows | File system / Azure Storage blobs | Raw HTTP requests in W3C extended log format |
| Detailed error messages | Windows | File system | HTML error pages for HTTP 400+ (not sent to clients in production) |
| Failed request tracing | Windows | File system | IIS component trace per failed request (XML + XSL) |
| Deployment logging | Windows, Linux | File system | Deployment failure reasons; always enabled |

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_5-enable-diagnostic-logging.pdf
> "There are built-in diagnostics to assist with debugging an App Service app."

## Key Facts

- Application logging on the file system auto-disables after **12 hours**.
- For production, prefer **Azure Storage blobs** for long-term retention.
- Deployment logging is **always on** and cannot be disabled.
- Windows-only types: Web server logging, Detailed error messages, Failed request tracing.

## Accessing Logs

- **Live log streaming**: Azure portal or Azure CLI.
- **File system logs**: Kudu console or FTP.
- **Azure Storage blobs**: for long-term retention.

## Related Pages

- [[diagnostic-logging]] – concept page
- [[configure-web-app-settings-introduction]] – module intro
- [[azure-app-service]] – the service being monitored
