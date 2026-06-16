---
title: "Explore Managed Identities"
type: source
tags: [managed-identity, azure, entra-id, az204, security]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_2-managed-identities-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Managed Identities

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_2-managed-identities-overview.pdf

## Overview

[[managed-identity|Managed identities]] eliminate the need for developers to manage secrets, credentials, certificates, and keys used to secure communication between services. They provide an automatically managed identity in [[microsoft-entra-id]] for applications to connect to resources that support Microsoft Entra authentication.

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_2-managed-identities-overview.pdf
> "Applications can use managed identities to obtain Microsoft Entra tokens without having to manage any credentials."

## Key Claims

- Managed identities are internally **service principals of a special type**, locked to only be used with Azure resources.
- When a managed identity is deleted, the corresponding service principal is automatically removed.
- Applications obtain [[microsoft-entra-id]] access tokens without storing or rotating credentials.

## Types of Managed Identities

### System-Assigned

- Enabled directly on an Azure service instance.
- Azure creates an identity for the instance in the Microsoft Entra tenant.
- **Lifecycle is tied to the Azure service instance** — if the instance is deleted, the identity and credentials are automatically cleaned up.
- Cannot be shared: associated with a single Azure resource only.
- Use cases: workloads contained within a single Azure resource; workloads needing independent identities.

### User-Assigned

- Created as a **standalone Azure resource**.
- Lifecycle is managed independently from any Azure service instance — must be explicitly deleted.
- Can be shared: the same user-assigned identity can be assigned to multiple Azure service instances.
- Use cases: workloads running on multiple resources sharing a single identity; workloads needing preauthorization to a secure resource as part of a provisioning flow; workloads where resources are recycled frequently but permissions should stay consistent.

## Characteristics Comparison

| Property | System-assigned | User-assigned |
|---|---|---|
| Creation | Part of an Azure resource (VM, App Service, etc.) | Standalone Azure resource |
| Lifecycle | Shared with parent resource | Independent; must be explicitly deleted |
| Sharing | Single resource only | Can be shared across multiple resources |

## Data Points

- Supported by any Azure resource that supports Microsoft Entra authentication.
- Module examples use Azure Virtual Machines, but concepts apply broadly.

## Related Pages

- [[managed-identity]] – entity page
- [[microsoft-entra-id]] – identity provider
- [[managed-identities-authentication-flow]] – how the flow works in practice
- [[configure-managed-identities]] – CLI configuration commands
- [[acquire-access-token]] – obtaining tokens in code
