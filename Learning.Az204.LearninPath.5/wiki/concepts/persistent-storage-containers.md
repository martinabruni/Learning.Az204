---
title: "Persistent Storage for Containers"
type: concept
tags: [aci, storage, azure-files, volume-mount, stateful, az204]
sources: [aci-azure-file-share-mount.md, aci-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Persistent Storage for Containers

Containers are **stateless by default** — data is lost when a container crashes or stops. Persistent storage is achieved by mounting external volumes.

## ACI Volume Types

| Volume Type | Description |
|---|---|
| Azure file share | Fully managed SMB file share via [[azure-files]] |
| Secret | Inject secrets as files |
| Empty directory | Ephemeral shared storage between containers |
| Cloned git repo | Mount a git repository clone |

## Azure Files as Persistent Volume

- Most common option for persistent state in ACI.
- Uses SMB (CIFS) protocol.
- **Linux containers only**, must run as **root**.
- Provides similar file-sharing to using Azure Files with Azure VMs.

## Mounting a Single Volume (CLI)

```bash
--azure-file-volume-account-name $STORAGE_ACCOUNT \
--azure-file-volume-account-key $STORAGE_KEY \
--azure-file-volume-share-name $SHARE_NAME \
--azure-file-volume-mount-path /aci/logs/
```

## Mounting Multiple Volumes

Requires ARM template or YAML file — populate `volumes` array and `volumeMounts` per container.

## Related Pages

- [[azure-container-instances]] – entity page
- [[azure-files]] – entity page
- [[aci-azure-file-share-mount]] – source page with full examples
