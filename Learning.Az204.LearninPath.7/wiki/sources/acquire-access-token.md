---
title: "Acquire an Access Token"
type: source
tags: [managed-identity, azure-identity, defaultazurecredential, az204, security]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_5-acquire-access-token.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Acquire an Access Token

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_5-acquire-access-token.pdf

## Overview

Client applications can request a managed identity app-only access token via the **Azure Identity library**. The recommended type is `DefaultAzureCredential`, which works across both development and production environments without code changes.

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_5-acquire-access-token.pdf
> "DefaultAzureCredential is intended to simplify getting started with the SDK by handling common scenarios with reasonable default behaviors."

## DefaultAzureCredential Authentication Chain

`DefaultAzureCredential` attempts authentication mechanisms in this order, stopping at the first success:

1. **Environment** — reads account info from environment variables.
2. **Managed Identity** — if deployed to an Azure host with Managed Identity enabled.
3. **Visual Studio** — if authenticated via Visual Studio.
4. **Azure CLI** — if authenticated via `az login`.
5. **Azure PowerShell** — if authenticated via `Connect-AzAccount`.
6. **Interactive browser** — if enabled (disabled by default).

## Code Examples

### Install the package

```bash
dotnet add package Azure.Identity
```

### Authenticate with DefaultAzureCredential (system-assigned)

```csharp
// Create a secret client using the DefaultAzureCredential
var client = new SecretClient(
    new Uri("https://myvault.vault.azure.net/"),
    new DefaultAzureCredential());
```

### Specify a user-assigned managed identity

```csharp
string userAssignedClientId = "<your managed identity client Id>";
var credential = new DefaultAzureCredential(
    new DefaultAzureCredentialOptions {
        ManagedIdentityClientId = userAssignedClientId
    });

var blobClient = new BlobClient(
    new Uri("https://myaccount.blob.core.windows.net/mycontainer/myblob"),
    credential);
```

### Custom chain with ChainedTokenCredential

```csharp
// Authenticate using managed identity if available; otherwise fall back to Azure CLI.
var credential = new ChainedTokenCredential(
    new ManagedIdentityCredential(),
    new AzureCliCredential());

var eventHubProducerClient = new EventHubProducerClient(
    "myeventhub.eventhubs.windows.net", "myhubpath", credential);
```

## Key Claims

- `DefaultAzureCredential` requires **no code changes** when moving from local development to production — the authentication mechanism is picked up from the environment.
- `ChainedTokenCredential` allows advanced users to define a custom ordered credential chain.
- `ManagedIdentityCredential` can be used directly in production; `AzureCliCredential` serves as a local dev fallback.
- The Azure Identity library is available for .NET, Python, Java, and JavaScript.

## Data Points

- Package: `Azure.Identity` (NuGet for .NET).
- User-assigned identity is specified via `ManagedIdentityClientId` option on `DefaultAzureCredentialOptions`.

## Related Pages

- [[managed-identity]] – entity page
- [[default-azure-credential]] – concept page for the credential type
- [[microsoft-entra-id]] – token issuer
- [[azure-key-vault]] – common token target (SecretClient example)
- [[managed-identities-authentication-flow]] – low-level IMDS token flow
- [[configure-managed-identities]] – how to enable managed identity on a resource
