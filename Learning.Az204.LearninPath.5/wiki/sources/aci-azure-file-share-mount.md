---
title: "Mount an Azure File Share in Azure Container Instances"
type: source
tags: [aci, azure-files, volume-mount, persistent-storage, az204]
sources: [learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_6-mount-azure-file-share-azure-container-instances.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Mount an Azure File Share in Azure Container Instances

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_6-mount-azure-file-share-azure-container-instances.pdf

## Overview

By default, [[azure-container-instances]] are **stateless** — all state is lost when a container crashes or stops. To persist state, mount a volume from an external store. [[azure-files]] shares are the primary external volume type supported.

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_6-mount-azure-file-share-azure-container-instances.pdf
> "Azure Files offers fully managed file shares in the cloud that are accessible via the industry standard Server Message Block (SMB) protocol."

## Key Claims

- Azure file share volumes enable file-sharing similar to using Azure Files with Azure VMs.
- Azure Files uses **SMB protocol**.

## Limitations

- Azure file shares can only be mounted to **Linux containers**.
- The Linux container must run as **root**.
- Volume mounts are limited to **CIFS support**.

## Deploy and Mount via Azure CLI

```bash
az container create \
    --resource-group $ACI_PERS_RESOURCE_GROUP \
    --name hellofiles \
    --image mcr.microsoft.com/azuredocs/aci-hellofiles \
    --dns-name-label aci-demo \
    --ports 80 \
    --azure-file-volume-account-name $ACI_PERS_STORAGE_ACCOUNT_NAME \
    --azure-file-volume-account-key $STORAGE_KEY \
    --azure-file-volume-share-name $ACI_PERS_SHARE_NAME \
    --azure-file-volume-mount-path /aci/logs/
```

> The `--dns-name-label` value must be unique within the Azure region.

## Deploy and Mount via YAML

YAML is the **preferred method** when deploying multi-container groups. Key YAML fields:

```yaml
volumeMounts:
  - mountPath: /aci/logs/
    name: filesharevolume
volumes:
  - name: filesharevolume
    azureFile:
      shareName: acishare
      storageAccountName: <Storage account name>
      storageAccountKey: <Storage account key>
```

## Mount Multiple Volumes

- Requires an ARM template or YAML file.
- Populate the `volumes` array in the template properties section.
- Populate the `volumeMounts` array in each container definition.

## Related Pages

- [[azure-container-instances]] – entity page
- [[azure-files]] – entity page
- [[aci-overview]] – ACI overview source
- [[persistent-storage-containers]] – concept page
