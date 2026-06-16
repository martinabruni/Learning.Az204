---
title: "Blob Access Tiers"
type: concept
tags: [blob-storage, access-tiers, hot, cool, cold, archive, cost-optimization, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-blob-storage_2-blob-storage-overview.pdf,
          learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_2-blob-storage-lifecycle.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Blob Access Tiers

## Definition

Azure Storage access tiers allow you to store block blob data in the most cost-effective manner based on usage patterns. Each tier trades off storage cost against access cost.

## Tiers at a Glance

| Tier | Type | Min Storage | Storage Cost | Access Cost | Retrieval Latency |
|---|---|---|---|---|---|
| Hot | Online | None | Highest | Lowest | Immediate |
| Cool | Online | 30 days | Lower than Hot | Higher than Hot | Immediate |
| Cold | Online | 90 days | Lower than Cool | Higher than Cool | Immediate |
| Archive | Offline | 180 days | Lowest | Highest | Hours |

- New storage accounts are created in the **Hot** tier by default.
- Data storage limits are set at the **account level**, not per tier.
- Tiers can be switched at any time.
- Archive tier is available only for **individual block blobs** (not at account/container level).

## When to Use Each Tier

| Scenario | Recommended Tier |
|---|---|
| Actively read/modified data | Hot |
| Infrequently accessed; needed quickly | Cool |
| Rarely accessed; long-term retention | Cold |
| Archival; tolerate hours of delay | Archive |

## Archive Tier Specifics

- Blob is **offline** in the archive tier — cannot be read or modified directly.
- Must be **rehydrated** (copied to Hot/Cool or tier changed) before access.
- See [[rehydrate-blob-data]] for rehydration options and priority settings.

## Cost Warning

Removing data from Cool or Cold before the minimum duration incurs an **early deletion charge**.

## Related Pages

- [[blob-lifecycle-management]] – automated tier transitions
- [[blob-storage-overview]] – source: access tier definitions
- [[blob-storage-lifecycle]] – source: lifecycle and tier overview
- [[rehydrate-blob-data]] – source: rehydrating archive blobs
- [[azure-blob-storage]] – entity: the service
