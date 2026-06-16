---
title: "DefaultAzureCredential"
type: concept
tags: [azure-identity, managed-identity, authentication, sdk, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_5-acquire-access-token.pdf,
          learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# DefaultAzureCredential

## What It Is

`DefaultAzureCredential` is a credential type from the **Azure Identity library** that automatically attempts authentication via multiple mechanisms in a defined order, stopping at the first success. It enables applications to work seamlessly in both local development and production Azure environments without code changes.

## Authentication Chain (in order)

| Priority | Mechanism | Trigger |
|----------|-----------|---------|
| 1 | **Environment** | Environment variables with account info |
| 2 | **Managed Identity** | Deployed to an Azure host with managed identity enabled |
| 3 | **Visual Studio** | Developer authenticated via Visual Studio |
| 4 | **Azure CLI** | Developer authenticated via `az login` |
| 5 | **Azure PowerShell** | Developer authenticated via `Connect-AzAccount` |
| 6 | **Interactive browser** | If explicitly enabled (disabled by default) |

## Why It Matters

- No credential management in code.
- Same code works locally (using developer credentials) and in production (using managed identity).
- Removes the need to branch logic based on environment.

## Code Examples

```csharp
// System-assigned or environment-based auth
var credential = new DefaultAzureCredential();

// Specify a user-assigned managed identity
var credential = new DefaultAzureCredential(new DefaultAzureCredentialOptions {
    ManagedIdentityClientId = "<your managed identity client Id>"
});
```

## ChainedTokenCredential

For advanced scenarios, `ChainedTokenCredential` lets users define a custom ordered credential chain:

```csharp
var credential = new ChainedTokenCredential(
    new ManagedIdentityCredential(),
    new AzureCliCredential());
```

This is useful to explicitly try managed identity and fall back to Azure CLI if managed identity is not available.

## Package

```bash
dotnet add package Azure.Identity
```

## Availability

Available in .NET, Python, Java, and JavaScript Azure Identity SDKs.

## Related Pages

- [[managed-identity]] – the identity type used in production
- [[acquire-access-token]] – source with full code examples
- [[azure-key-vault]] – common target (SecretClient)
- [[microsoft-entra-id]] – token issuer
