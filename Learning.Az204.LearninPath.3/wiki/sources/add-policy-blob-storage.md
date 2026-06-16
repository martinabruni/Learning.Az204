---
title: "Implement Blob Storage Lifecycle Policies"
type: source
tags: [blob-storage, lifecycle-management, azure-portal, azure-cli, az204]
sources: [learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_4-add-policy-blob-storage.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Implement Blob Storage Lifecycle Policies

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_4-add-policy-blob-storage.pdf

## Overview

Lifecycle management policies can be added, edited, or removed using multiple tools. The policy must be written and read in full — **partial updates are not supported**.

## Key Claims

### Supported Tools

- Azure portal (List view or Code view)
- Azure PowerShell
- Azure CLI
- REST APIs

### Azure Portal — Code View Steps

1. Navigate to the storage account in the Azure portal.
2. Under **Data management**, select **Lifecycle Management**.
3. Select the **Code View** tab.
4. Define the policy in JSON.

### Azure CLI

```bash
az storage account management-policy create \
    --account-name <storage-account> \
    --policy @policy.json \
    --resource-group <resource-group>
```

Write the policy to a JSON file first, then call `az storage account management-policy create`.

### Example Policy (move `log` blobs to Cool after 30 days)

```json
{
  "rules": [
    {
      "enabled": true,
      "name": "move-to-cool",
      "type": "Lifecycle",
      "definition": {
        "actions": {
          "baseBlob": {
            "tierToCool": { "daysAfterModificationGreaterThan": 30 }
          }
        },
        "filters": {
          "blobTypes": ["blockBlob"],
          "prefixMatch": ["sample-container/log"]
        }
      }
    }
  ]
}
```

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_4-add-policy-blob-storage.pdf
> "A lifecycle management policy must be read or written in full. Partial updates aren't supported."

## Related Pages

- [[blob-lifecycle-management]] – concept: lifecycle policy framework
- [[blob-lifecycle-policies]] – source: policy structure, filters, and actions
- [[blob-storage-lifecycle]] – source: access tiers and lifecycle intro
- [[azure-blob-storage]] – entity page
