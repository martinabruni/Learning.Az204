---
title: "Configure Path Mappings"
type: source
tags: [app-service, configuration, iis, containers, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Configure Path Mappings

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf

## Overview

The **Configuration → Path mappings** section configures handler mappings and virtual application/directory mappings. Options differ by OS type.

## Windows Apps (Uncontainerized)

### Handler Mappings

Custom script processors for specific file extensions:

| Field | Description |
|-------|-------------|
| Extension | e.g. `*.php` or `handler.fcgi` |
| Script processor | Absolute path, e.g. `D:\home\site\wwwroot` |
| Arguments | Optional command-line args for the processor |

### Virtual Applications and Directories

- Default root `/` → `D:\home\site\wwwroot`.
- Edit or add virtual directories mapped to physical paths relative to `D:\home`.
- Clear the **Directory** checkbox to mark as a web application.

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf
> "Each app has the default root path (/) mapped to D:\home\site\wwwroot, where your code is deployed by default."

## Linux and Containerized Apps

Custom Azure Storage Mounts:

| Field | Description |
|-------|-------------|
| Name | Display name |
| Configuration options | Basic or Advanced (Key Vault / private endpoints) |
| Storage accounts | Target storage account |
| Mount path | Virtual path inside the container |

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf
> "Containerized apps include all Linux apps and also the Windows and Linux custom containers running on App Service."

## Related Pages

- [[path-mappings]] – concept page
- [[configure-web-app-settings-introduction]] – module intro
- [[container-deployment]] – container-specific configuration
