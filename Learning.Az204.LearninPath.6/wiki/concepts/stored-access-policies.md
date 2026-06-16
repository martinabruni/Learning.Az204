---
title: "Stored Access Policies"
type: concept
tags: [sas, stored-access-policy, azure-storage, revocation, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_4-stored-access-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Stored Access Policies

## What It Is

A stored access policy provides **server-side control** over service-level SAS. It groups one or more SAS tokens under a named policy, enabling modification or revocation of those SAS tokens after they are issued.

## Supported Storage Resources

- Blob containers
- File shares
- Queues
- Tables

## Policy Parameters

- **Start time** — when access begins.
- **Expiry time** — when access ends.
- **Permissions** — the allowed operations.

Parameters can be split between the policy and the SAS URI, but a parameter cannot be in both simultaneously.

## Creating a Policy

- Call the **Set ACL operation** for the resource with a signed identifier (up to 64 characters) and optional access parameters.
- Takes **up to 30 seconds** to take effect (HTTP 403 during propagation is possible).
- Table entity range restrictions cannot be in a stored access policy.

## Modifying or Revoking

| Action | Effect |
|--------|--------|
| Modify policy parameters | Update affects all associated SAS |
| Delete the policy | Immediately revokes all associated SAS |
| Change signed identifier | Breaks all existing SAS associations |
| Set expiry in the past | All associated SAS expire immediately |

## Related Pages

- [[shared-access-signature]] – the SAS mechanism this policy controls
- [[sas-overview]] – SAS types and anatomy
- [[stored-access-policies]] – source page
