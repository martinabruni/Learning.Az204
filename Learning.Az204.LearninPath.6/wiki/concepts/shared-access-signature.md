---
title: "Shared Access Signature (SAS)"
type: concept
tags: [sas, azure-storage, security, authorization, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_2-shared-access-signatures-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_3-shared-access-signatures.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Shared Access Signature (SAS)

## What It Is

A SAS is a **signed URI** that delegates limited, time-bound access to Azure Storage resources without sharing the storage account key. It is constructed from a resource URI plus a SAS token containing access parameters and a cryptographic signature.

## Three Types

| Type | Secured With | Applies To |
|------|-------------|-----------|
| **User delegation SAS** | Microsoft Entra credentials | Blob Storage, Data Lake Storage |
| **Service SAS** | Storage account key | Single service (Blob, Queue, Table, or Files) |
| **Account SAS** | Storage account key | One or more storage services; superset of service SAS |

Best practice: prefer **user delegation SAS** when possible.

## SAS Token Parameters

| Parameter | Meaning |
|-----------|---------|
| `sp` | Permissions: a=add, c=create, d=delete, l=list, r=read, w=write |
| `st` | Start time (UTC) |
| `se` | Expiry time (UTC) |
| `sv` | Storage API version |
| `sr` | Resource type (b=blob, etc.) |
| `sig` | Cryptographic signature |

## Use Cases

- Providing clients with access to storage without exposing account keys.
- Two design patterns: **front-end proxy** (validates business rules) or **SAS provider service** (lightweight auth + direct client access to storage).
- Required for cross-account copy operations between blobs/files.

## Best Practices

- Always use **HTTPS**.
- Set the **smallest useful expiry time**.
- Grant **minimum required privileges** only.
- Use [[stored-access-policies]] for server-side revocation capability.
- When unacceptable risk: use a **middle-tier service** instead.

## Related Pages

- [[stored-access-policies]] – adds server-side revocation to SAS
- [[microsoft-entra-id]] – used for user delegation SAS
- [[sas-overview]] – source page covering types and anatomy
- [[sas-use-cases]] – source page covering design patterns and copy operations
