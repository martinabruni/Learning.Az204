---
title: "Choose When to Use Shared Access Signatures"
type: source
tags: [sas, shared-access-signature, azure-storage, design-patterns, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_3-shared-access-signatures.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Choose When to Use Shared Access Signatures

> [!source] learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_3-shared-access-signatures.pdf

## Overview

Use a [[shared-access-signature|SAS]] to provide secure access to storage resources for clients who don't otherwise have permissions.

## Key Claims

### Design Patterns for SAS Usage

**Pattern 1 — Front-end proxy service:**
- Clients upload/download data via a proxy that performs authentication.
- Advantage: allows business rule validation.
- Disadvantage: expensive/difficult to scale for large data volumes or high-volume transactions.

**Pattern 2 — SAS provider service (recommended for scale):**
- A lightweight service authenticates the client and generates a SAS.
- Client accesses storage directly using the SAS.
- Eliminates routing all data through a proxy.

**Hybrid approach:** process/validate data via front-end proxy; save/read directly via SAS.

### Copy Operations Requiring SAS

SAS is required on the **source object** in these copy scenarios:
- Copying a blob to another blob in a **different storage account** (SAS required for source; optional for destination).
- Copying a file to another file in a **different storage account** (SAS required for source; optional for destination).
- Copying a **blob to a file** or **file to a blob**, even within the **same storage account**.

## Related Pages

- [[shared-access-signature]] – SAS concept page
- [[sas-overview]] – SAS types, token anatomy, best practices
- [[stored-access-policies]] – server-side access control for SAS
