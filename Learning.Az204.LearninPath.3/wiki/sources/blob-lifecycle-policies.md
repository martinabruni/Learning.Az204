---
title: "Discover Blob Storage Lifecycle Policies"
type: source
tags: [blob-storage, lifecycle-management, policies, rules, az204]
sources: [learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_3-blob-storage-lifecycle-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Blob Storage Lifecycle Policies

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_3-blob-storage-lifecycle-policies.pdf

## Overview

A lifecycle management policy is a **JSON document** containing a collection of rules. Each rule has a filter set (scope) and an action set (what to do).

## Key Claims

### Policy Structure

- A policy requires at least one rule; supports up to **100 rules**.
- Each rule has: `name`, `enabled`, `type` (always `"Lifecycle"`), `definition` (filter + actions).

```json
{
  "rules": [
    { "name": "rule1", "enabled": true, "type": "Lifecycle", "definition": {...} }
  ]
}
```

### Rule Parameters

| Parameter | Type | Required | Notes |
|---|---|---|---|
| `name` | String | Yes | Up to 256 alphanumeric chars; case-sensitive; unique within policy |
| `enabled` | Boolean | No | Default is `true`; can disable rules temporarily |
| `type` | Enum | Yes | Currently only `"Lifecycle"` is valid |
| `definition` | Object | Yes | Contains filter set and action set |

### Rule Filters

Filters limit rule scope. Multiple filters are combined with logical AND.

| Filter | Type | Required |
|---|---|---|
| `blobTypes` | Array of enum values | Yes |
| `prefixMatch` | Array of strings (up to 10 prefixes) | No |
| `blobIndexMatch` | Array of dictionary values (up to 10 tag conditions) | No |

### Rule Actions

| Action | Current Version | Snapshot | Previous Versions |
|---|---|---|---|
| `tierToCool` | blockBlob | Supported | Supported |
| `tierToCold` | blockBlob | Supported | Supported |
| `enableAutoTierToHotFromCool` | blockBlob | Not supported | Not supported |
| `tierToArchive` | blockBlob | Supported | Supported |
| `delete` | blockBlob + appendBlob | Supported | Supported |

### Run Conditions

| Condition | Applies To |
|---|---|
| `daysAfterModificationGreaterThan` | Base blob actions |
| `daysAfterCreationGreaterThan` | Blob snapshot actions |
| `daysAfterLastAccessTimeGreaterThan` | Current version when access tracking enabled |
| `daysAfterLastTierChangeGreaterThan` | `tierToArchive` only — minimum days in online tier before re-archiving |

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_3-blob-storage-lifecycle-policies.pdf
> "If you define more than one action on the same blob, lifecycle management applies the least expensive action to the blob. For example, action delete is cheaper than action tierToArchive. Action tierToArchive is cheaper than action tierToCool."

### Sample Rule (complete JSON)

Applies to blockBlobs in `sample-container` with prefix `blob1`:
- Cool after 30 days since modification
- Archive after 90 days since modification (with 7-day minimum after last tier change)
- Delete after 2,555 days (7 years) since modification
- Delete snapshots after 90 days since creation

## Related Pages

- [[blob-lifecycle-management]] – concept: lifecycle policy framework
- [[blob-storage-lifecycle]] – source: access tiers and lifecycle introduction
- [[add-policy-blob-storage]] – source: implementing policies via Portal/CLI
- [[azure-blob-storage]] – entity page
