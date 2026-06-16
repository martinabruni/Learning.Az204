---
title: "Rehydrate Blob Data from the Archive Tier"
type: source
tags: [blob-storage, archive, rehydration, access-tiers, az204]
sources: [learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_5-rehydrate-blob-data.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Rehydrate Blob Data from the Archive Tier

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_5-rehydrate-blob-data.pdf

## Overview

Blobs in the archive tier are **offline** and cannot be read or modified. To access archived data, you must first rehydrate it to an online tier (Hot or Cool).

## Key Claims

### Rehydration Methods

Two options are available:

1. **Copy archived blob to an online tier** (recommended for most scenarios):
   - Use the `Copy Blob` or `Copy Blob from URL` operation.
   - Source blob remains unmodified in archive.
   - Must copy to a different blob name or different container — cannot overwrite source.
   - Since service version 2021-02-12: can copy to a different storage account in the same region.

2. **Change a blob's access tier to an online tier**:
   - Use the `Set Blob Tier` operation to change to Hot or Cool.
   - Once initiated, the operation **cannot be canceled**.
   - The tier continues to show as archived during the operation until complete.

> [!source] learn.microsoft.com_en-us_training_modules_manage-azure-blob-storage-lifecycle_5-rehydrate-blob-data.pdf
> "Caution: Changing a blob's tier doesn't affect its last modified time. If there is a lifecycle management policy in effect for the storage account, then rehydrating a blob with Set Blob Tier can result in a scenario where the lifecycle policy moves the blob back to the archive tier after rehydration because the last modified time is beyond the threshold set for the policy."

### Rehydration Priority

Set via the `x-ms-rehydrate-priority` header on `Set Blob Tier` or `Copy Blob`/`Copy Blob From URL`.

| Priority | Time to Complete |
|---|---|
| Standard | Processed in order received; may take up to **15 hours** |
| High | Prioritized; may complete in **under 1 hour** for objects under 10 GB |

- Check current rehydration priority by calling `Get Blob Properties` — returns `x-ms-rehydrate-priority` value (`Standard` or `High`).
- Microsoft recommends rehydrating **larger blobs** for optimal performance.
- Rehydrating many small blobs concurrently might require extra time.

## Related Pages

- [[blob-access-tiers]] – concept: Hot, Cool, Cold, Archive tiers
- [[blob-lifecycle-management]] – concept: lifecycle policies
- [[blob-storage-lifecycle]] – source: access tiers overview
- [[azure-blob-storage]] – entity page
