---
title: "Managed Identity"
type: entity
tags: [managed-identity, azure, entra-id, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_2-managed-identities-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf,
          learn.microsoft.com_en-us_training_modules_implement-managed-identities_4-configure-managed-identities.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Managed Identity

## What It Is

A managed identity is an automatically managed identity in [[microsoft-entra-id]] that applications use to authenticate to services supporting Microsoft Entra authentication — without storing, managing, or rotating credentials. Internally, managed identities are **service principals of a special type**, locked to be used only with Azure resources.

## Types

| Type | Creation | Lifecycle | Sharing |
|------|----------|-----------|---------|
| **System-assigned** | Created as part of an Azure resource | Deleted when parent resource is deleted | Cannot be shared; 1:1 with resource |
| **User-assigned** | Created as a standalone Azure resource | Independent; must be explicitly deleted | Can be shared across multiple resources |

## Common Use Cases

**System-assigned:**
- Workloads running on a single Azure resource.
- Workloads needing independent identities per resource.

**User-assigned:**
- Workloads running on multiple resources that share a single identity.
- Workloads needing preauthorization to a secure resource (provisioning flow).
- Workloads where resources are recycled frequently but permissions should stay consistent.

## Supported Services

Any Azure resource supporting Microsoft Entra authentication can use managed identities. Common services include: Azure Virtual Machines, Azure App Service, Azure Functions, Azure App Configuration.

## Authentication Recommendation

Using managed identities is the **recommended** (best practice) way to authenticate to [[azure-key-vault]] and other Microsoft Entra-protected services, as it eliminates the need to manage any bootstrap secret.

## CLI Commands (Azure VM)

```bash
# System-assigned: enable at VM creation
az vm create --assign-identity ...

# System-assigned: enable on existing VM
az vm identity assign -g <RG> -n <VM>

# User-assigned: create
az identity create -g <RG> -n <IDENTITY_NAME>

# User-assigned: assign to VM
az vm identity assign -g <RG> -n <VM> --identities <IDENTITY_NAME>
```

## Related Pages

- [[microsoft-entra-id]] – identity provider that issues tokens
- [[azure-key-vault]] – common target for managed identity authentication
- [[azure-app-configuration]] – supports managed identity for customer-managed key encryption
- [[explore-managed-identities]] – types and characteristics (source)
- [[managed-identities-authentication-flow]] – step-by-step token acquisition flow
- [[configure-managed-identities]] – CLI configuration examples
- [[acquire-access-token]] – SDK-level code using DefaultAzureCredential
- [[default-azure-credential]] – SDK credential type
