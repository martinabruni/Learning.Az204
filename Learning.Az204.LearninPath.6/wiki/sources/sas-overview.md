---
title: "Discover Shared Access Signatures (Overview)"
type: source
tags: [sas, shared-access-signature, azure-storage, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_2-shared-access-signatures-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Shared Access Signatures (Overview)

> [!source] learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_2-shared-access-signatures-overview.pdf

## Overview

A [[shared-access-signature|Shared Access Signature (SAS)]] is a **signed URI** pointing to one or more storage resources. It includes a token with query parameters indicating how resources may be accessed and a cryptographic signature authorizing the access.

## Key Claims

### Types of SAS

| Type | Secured with | Scope |
|------|-------------|-------|
| **User delegation SAS** | Microsoft Entra credentials + specified permissions | Blob Storage and Data Lake Storage only |
| **Service SAS** | Storage account key | Single service: Blob, Queue, Table, or Azure Files |
| **Account SAS** | Storage account key | One or more storage services; superset of service SAS capabilities |

> [!source] learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_2-shared-access-signatures-overview.pdf
> "Microsoft recommends that you use Microsoft Entra credentials when possible as a security best practice, rather than using the account key, which can be more easily compromised."

### How SAS Works

A SAS URI = base resource URI + SAS token. Example token parameters:

| Parameter | Description |
|-----------|-------------|
| `sp=r` | Access rights: a=add, c=create, d=delete, l=list, r=read, w=write |
| `st=...` | Access start date/time (UTC) |
| `se=...` | Access end date/time (UTC) |
| `sv=...` | Storage API version |
| `sr=b` | Storage resource type (b=blob) |
| `sig=...` | Cryptographic signature |

### Best Practices

- Always use **HTTPS** when distributing a SAS (prevents man-in-the-middle attacks).
- Prefer **user delegation SAS** (Entra credentials) over account key SAS.
- Set the **smallest useful expiration time**.
- Apply **minimum-required privileges** (grant only what's needed).
- When the risk of SAS is unacceptable, use a **middle-tier service** to manage access instead.

## Related Pages

- [[shared-access-signature]] – concept page
- [[sas-use-cases]] – when to use SAS
- [[stored-access-policies]] – server-side policy grouping for SAS
- [[microsoft-entra-id]] – preferred credential source for user delegation SAS
