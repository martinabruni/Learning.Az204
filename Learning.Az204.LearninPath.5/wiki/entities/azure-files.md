---
title: "Azure Files"
type: entity
tags: [azure-files, storage, smb, az204]
sources: [aci-azure-file-share-mount.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Files

Azure Files is a **fully managed cloud file share service** accessible via the industry-standard SMB (Server Message Block) protocol.

## Key Attributes

| Attribute | Value |
|---|---|
| Type | Managed cloud file share |
| Protocol | SMB (Server Message Block) / CIFS |
| Use with ACI | Mount as persistent volume in Linux containers |

## Usage with Azure Container Instances

- ACI containers are stateless by default — mounting an Azure Files share provides persistence.
- Limitations: Linux containers only, container must run as root, CIFS only.
- Provides file-sharing features comparable to using Azure Files with Azure Virtual Machines.

## Related Pages

- [[azure-container-instances]] – entity page
- [[aci-azure-file-share-mount]] – source page with CLI and YAML examples
- [[persistent-storage-containers]] – concept page
