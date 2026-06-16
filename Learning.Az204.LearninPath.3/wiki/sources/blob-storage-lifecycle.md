---
title: "Explore the Azure Blob Storage Lifecycle"
type: source
tags: [blob-storage, lifecycle-management, access-tiers, az204]
sources: [learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore the Azure Blob Storage Lifecycle

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf

## Overview

Data has unique lifecycles — frequently accessed early on, then less and less. [[blob-lifecycle-management]] provides a rule-based policy to automatically transition blobs between access tiers or expire them at end-of-life.

## Key Claims

### Access Tiers

| Tier | Type | Min Storage | Notes |
|---|---|---|---|
| Hot | Online | None | Frequent access; highest storage cost, lowest access cost |
| Cool | Online | 30 days | Infrequent access |
| Cold | Online | 90 days | Lower storage cost than Cool, higher access cost |
| Archive | Offline | 180 days | Rarely accessed; flexible latency (hours); cheapest storage |

- Data storage limits are set at the **account level**, not per access tier.
- You can spread your storage limit across all four tiers.

### Lifecycle Management Capabilities

With a lifecycle management policy you can:
- Transition blobs from cool to hot immediately when accessed (performance optimization).
- Transition current versions, previous versions, or snapshots to cooler tiers after a period of inactivity.
- Delete current versions, previous versions, or snapshots at the end of their lifecycles.
- Apply rules to: the entire storage account, selected containers, or a subset of blobs using name prefixes or blob index tags.

### Cost-Optimization Scenario

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf
> "By moving data to the appropriate storage tier based on its age with lifecycle management policy rules, you can design the least expensive solution for your needs."

Example: data accessed frequently → hot; occasionally after 2 weeks → cool; rarely after 1 month → archive.

## Related Pages

- [[azure-blob-storage]] – entity page
- [[blob-access-tiers]] – concept: Hot, Cool, Cold, Archive
- [[blob-lifecycle-management]] – concept: lifecycle policies
- [[blob-lifecycle-policies]] – source: policy structure and rules
- [[add-policy-blob-storage]] – source: implementing policies
- [[rehydrate-blob-data]] – source: rehydrating from archive
