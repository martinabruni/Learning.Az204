---
title: "Explore Stored Access Policies"
type: source
tags: [sas, stored-access-policy, azure-storage, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_4-stored-access-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Stored Access Policies

> [!source] learn.microsoft.com_en-us_training_modules_implement-shared-access-signatures_4-stored-access-policies.pdf

## Overview

A [[stored-access-policies|stored access policy]] provides an **extra level of server-side control** over service-level SAS. It groups SAS signatures and adds more restrictions, including the ability to revoke after issuance.

## Key Claims

### Supported Storage Resources

- Blob containers
- File shares
- Queues
- Tables

### Creating a Stored Access Policy

- Access policy parameters: start time, expiry time, permissions.
- Parameters can be split between the SAS URI and the stored access policy — but the **same parameter cannot appear in both**.
- Created by calling the **Set ACL operation** on the resource, with a signed identifier (up to 64 characters) and optional access parameters.
- Takes **up to 30 seconds** to take effect; requests may return HTTP 403 during propagation.
- Table entity range restrictions (`startpk`, `startrk`, `endpk`, `endrk`) **cannot** be in a stored access policy.

### C# Example

```csharp
BlobSignedIdentifier identifier = new BlobSignedIdentifier
{
    Id = "stored access policy identifier",
    AccessPolicy = new BlobAccessPolicy
    {
        ExpiresOn = DateTimeOffset.UtcNow.AddHours(1),
        Permissions = "rw"
    }
};
blobContainer.SetAccessPolicy(permissions: new BlobSignedIdentifier[] { identifier });
```

### Azure CLI Example

```bash
az storage container policy create \
    --name <stored access policy identifier> \
    --container-name <container name> \
    --start <start time UTC> \
    --expiry <expiry time UTC> \
    --permissions <(a)dd,(c)reate,(d)elete,(l)ist,(r)ead,(w)rite> \
    --account-key <storage account key> \
    --account-name <storage account name>
```

### Modifying or Revoking

- **Modify**: call the Set ACL operation with updated parameters.
- **Revoke** by:
  - Deleting the policy.
  - Renaming it (changing the signed identifier breaks associations with existing SAS).
  - Setting expiry time to a value in the past.
- Deleting or modifying a stored access policy **immediately affects all associated SAS**.

## Related Pages

- [[stored-access-policies]] – concept page
- [[shared-access-signature]] – the SAS mechanism it controls
- [[sas-overview]] – SAS types and token anatomy
