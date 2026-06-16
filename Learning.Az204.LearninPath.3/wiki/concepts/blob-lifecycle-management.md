---
title: "Blob Lifecycle Management"
type: concept
tags: [blob-storage, lifecycle-management, tiering, policies, cost-optimization, az204]
sources: [learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf,
          learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_3-blob-storage-lifecycle-policies.pdf,
          learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_4-add-policy-blob-storage.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Blob Lifecycle Management

## Definition

Azure Blob Storage Lifecycle Management is a **rule-based policy system** that automates the transition of blob data between access tiers and the deletion of expired data. It enables cost optimization aligned with data access patterns over time.

## Core Capabilities

- Transition blobs from cool to hot immediately when accessed.
- Transition blobs to cooler tiers after a period of inactivity.
- Delete blobs at the end of their lifecycle.
- Apply rules to an entire account, selected containers, or a subset of blobs (by name prefix or blob index tags).

## Policy Structure

A policy is a JSON document containing up to **100 rules**. Each rule has:
- **Filter set**: limits which blobs the rule applies to (`blobTypes`, `prefixMatch`, `blobIndexMatch`).
- **Action set**: what to do (`tierToCool`, `tierToCold`, `tierToArchive`, `delete`, `enableAutoTierToHotFromCool`).

```json
{
  "rules": [
    {
      "name": "rule-name",
      "enabled": true,
      "type": "Lifecycle",
      "definition": {
        "filters": { "blobTypes": ["blockBlob"], "prefixMatch": ["container/prefix"] },
        "actions": { "baseBlob": { "tierToCool": { "daysAfterModificationGreaterThan": 30 } } }
      }
    }
  ]
}
```

## Run Conditions

| Condition | Applies To |
|---|---|
| `daysAfterModificationGreaterThan` | Base blobs |
| `daysAfterCreationGreaterThan` | Snapshots |
| `daysAfterLastAccessTimeGreaterThan` | Current version (with access tracking) |
| `daysAfterLastTierChangeGreaterThan` | `tierToArchive` only |

## Action Priority Rule

When multiple actions apply to the same blob, lifecycle management applies the **least expensive action**:
`delete` < `tierToArchive` < `tierToCool`

## Tooling

Policies can be created/edited via:
- Azure portal (List view or Code view)
- Azure PowerShell
- Azure CLI (`az storage account management-policy create`)
- REST APIs

**Important**: policies must be read or written in full — **partial updates are not supported**.

## Related Pages

- [[blob-access-tiers]] – the tiers between which lifecycle management moves data
- [[blob-lifecycle-policies]] – source: full policy schema and examples
- [[add-policy-blob-storage]] – source: implementation steps
- [[blob-storage-lifecycle]] – source: lifecycle overview
- [[rehydrate-blob-data]] – source: reverse of archiving
- [[azure-blob-storage]] – entity page
