---
title: "Authenticate to Azure Key Vault"
type: source
tags: [key-vault, azure, authentication, entra-id, rest-api, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Authenticate to Azure Key Vault

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf

## Overview

Authentication to [[azure-key-vault]] uses [[microsoft-entra-id]], which authenticates any **security principal** — a user, group, or service principal — requesting access to Azure resources.

## Security Principals

| Principal Type | Description |
|---------------|-------------|
| **Users** | Real people with Microsoft Entra ID accounts |
| **Groups** | Collections of users; permissions apply to all members |
| **Service Principals** | Represent apps or services (not people); like a user account for an app |

## Obtaining a Service Principal for an App

Two ways:

1. **Use a managed identity (recommended)**: Azure creates and manages the service principal automatically. Works with App Service, Azure Functions, and Virtual Machines. No credentials stored.

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-key-vault_4-key-vault-authentication.pdf
> "It's recommended to use a system-assigned managed identity."

2. **Register the app manually**: Registers the app in Microsoft Entra ID, creating a service principal and an app object identifying the app across all tenants.

## Authentication in Application Code

The Key Vault SDK uses the **Azure Identity client library** (`DefaultAzureCredential`) for seamless authentication across environments with the same code.

| Language | SDK |
|----------|-----|
| .NET | Azure Identity SDK .NET |
| Python | Azure Identity SDK Python |
| Java | Azure Identity SDK Java |
| JavaScript | Azure Identity SDK JavaScript |

## Authentication with REST API

Access tokens must be sent in the HTTP `Authorization` header:

```http
PUT /keys/MYKEY?api-version=<api_version> HTTP/1.1
Authorization: Bearer <access_token>
```

When no token is supplied or the token is rejected, the service returns HTTP 401 with a `WWW-Authenticate` header:

```http
401 Not Authorized
WWW-Authenticate: Bearer authorization="...", resource="..."
```

`WWW-Authenticate` parameters:
- `authorization`: The OAuth2 authorization service address to obtain a token.
- `resource`: The resource name (`https://vault.azure.net`) to use in the authorization request.

## Key Claims

- Key Vault authentication is delegated entirely to Microsoft Entra ID.
- The Azure Identity client library provides a unified `DefaultAzureCredential` type that works across all environments.
- REST-based callers must include a Bearer token in the Authorization header.

## Related Pages

- [[azure-key-vault]] – entity page
- [[managed-identity]] – recommended service principal method
- [[microsoft-entra-id]] – authentication provider
- [[key-vault-best-practices]] – best practices including auth method comparison
- [[default-azure-credential]] – SDK credential type
