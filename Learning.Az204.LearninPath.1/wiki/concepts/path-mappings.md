---
title: "Path Mappings"
type: concept
tags: [configuration, iis, virtual-directory, containers, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_4-configure-path-mappings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Path Mappings

## Definition

**Path mappings** define how URL paths map to physical directories or custom script processors in [[azure-app-service]]. Configuration varies by OS type.

## Windows Apps

### Handler Mappings
Custom script processors for specific file extensions (e.g. PHP via FastCGI):
- **Extension**: `*.php`
- **Script processor**: absolute path on disk
- **Arguments**: optional CLI args

### Virtual Applications and Directories
- Default `/` → `D:\home\site\wwwroot`
- Additional virtual directories mapped to physical paths under `D:\home`
- Marking as "web application" (vs. directory) affects IIS configuration

## Linux / Containerized Apps

**Azure Storage Mounts** allow mounting external storage inside the container:
- Basic: no private endpoints or Key Vault
- Advanced: supports service endpoints, private endpoints, Azure Key Vault

## Related Pages

- [[configure-path-mappings]] – source page
- [[azure-app-service]] – the platform
- [[container-deployment]] – container-specific storage considerations
- [[general-settings]] – other platform configuration
