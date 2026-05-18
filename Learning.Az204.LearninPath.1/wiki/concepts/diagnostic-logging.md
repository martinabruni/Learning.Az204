---
title: "Diagnostic Logging"
type: concept
tags: [diagnostics, logging, monitoring, debugging, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_5-enable-diagnostic-logging.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Diagnostic Logging

## Definition

**Diagnostic logging** refers to the built-in log collection capabilities in [[azure-app-service]] that help diagnose application and infrastructure issues.

## Log Types

| Type | Platform | Retention | Notes |
|------|----------|-----------|-------|
| Application logging | Windows, Linux | File system (12h auto-off) or Azure Blob | App-generated; Critical/Error/Warning/Info/Debug/Trace |
| Web server logging | Windows | File system or Azure Blob | W3C extended format; HTTP request details |
| Detailed error messages | Windows | File system | HTML pages for HTTP 400+ errors |
| Failed request tracing | Windows | File system | Detailed IIS component trace per failed request |
| Deployment logging | Windows, Linux | File system | Always on; deployment failure reasons |

## Storage Options

- **File system**: temporary, limited retention; use for short-term debugging.
- **Azure Storage blobs**: durable, long-term; recommended for production.

## Access Methods

- **Live log streaming**: Azure portal or `az webapp log tail` CLI command.
- **Kudu console**: browse file system logs (`https://<app>.scm.azurewebsites.net`).
- **FTP**: traditional file-level access.

## Key Notes

- Application logging (file system) automatically disables after **12 hours** to protect performance.
- Deployment logging is **always enabled** and cannot be disabled.
- Detailed error messages and Failed request tracing are **Windows only**.

## Related Pages

- [[enable-diagnostic-logging]] – source page
- [[azure-app-service]] – the monitored service
- [[general-settings]] – platform configuration
