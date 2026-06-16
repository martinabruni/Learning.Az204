---
title: "Key Vault Access Control"
type: concept
tags: [key-vault, azure, rbac, access-policy, authorization, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_2-key-vault-overview.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_3-key-vault-concepts.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Key Vault Access Control

## Overview

Access to [[azure-key-vault]] requires two things: **authentication** (who you are) and **authorization** (what you can do). Authentication is handled by [[microsoft-entra-id]]; authorization uses Azure RBAC or Key Vault access policies.

## Authentication Methods (Ranked by Recommendation)

| Method | Recommended? | Reason |
|--------|-------------|--------|
| **Managed identities** | Yes (best practice) | Azure auto-rotates credentials; no secret bootstrap problem |
| **Service principal + certificate** | Not recommended | Manual certificate rotation required |
| **Service principal + secret** | Not recommended | Bootstrap secret rotation is difficult to automate |

## Authorization Models

| Model | Scope |
|-------|-------|
| **Azure RBAC** | Vault management (control plane) AND data access (data plane) |
| **Key Vault access policy** | Data access (data plane) only |

## Data Plane vs. Control Plane

- **Control plane**: Creating, deleting, and configuring vaults. Managed via Azure RBAC.
- **Data plane**: Reading, writing, and using keys, secrets, and certificates. Managed via Azure RBAC or Key Vault access policy.

## REST API Authorization

Callers must provide a Bearer token in the HTTP Authorization header. If no valid token is provided, Key Vault returns:

```http
401 Not Authorized
WWW-Authenticate: Bearer authorization="...", resource="https://vault.azure.net"
```

The `resource` parameter (`https://vault.azure.net`) must be used when requesting the access token from [[microsoft-entra-id]].

## Related Pages

- [[azure-key-vault]] – entity page
- [[managed-identity]] – recommended authentication method
- [[microsoft-entra-id]] – authentication provider
- [[key-vault-authentication]] – source page with REST API details
- [[key-vault-best-practices]] – best practices source
