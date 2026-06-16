---
title: "Connect Functions to Azure Services"
type: source
tags: [azure-functions, security, managed-identity, application-settings, identity-based-connections, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Connect Functions to Azure Services

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf

## Overview

Azure Functions uses the [[application-settings]] functionality of Azure App Service to securely store connection strings, keys, and tokens. Application settings are stored **encrypted** and accessed at runtime as environment variable name-value pairs.

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf
> "For triggers and bindings that require a connection property, you set the application setting name instead of the actual connection string. You can't configure a binding directly with a connection string or key."

## Configuration Provider

The default provider uses **environment variables**:
- In Azure: defined in application settings.
- Locally: defined in `local.settings.json`.

## Identity-Based Connections

Some connections use a **managed identity** instead of a secret (connection string). Support depends on the extension.

- When hosted in Azure Functions: uses **system-assigned managed identity** by default.
- User-assigned identity: specify via `credential` and `clientID` properties. Configuring by resource ID is **not** supported.
- Local development: uses the **developer identity** (customizable).

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf
> "An app running in a Consumption or Elastic Premium plan, uses the WEBSITE_AZUREFILESCONNECTIONSTRING and WEBSITE_CONTENTSHARE settings when connecting to Azure Files on the storage account used by your function app. Azure Files doesn't support using managed identity when accessing the file share."

## Grant Permission to the Identity

Identities must have permissions to perform intended actions:
- Assign a role in **Azure RBAC**, or
- Specify the identity in an **access policy** (service-dependent).

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf
> "Where possible, adhere to the principle of least privilege, granting the identity only required privileges."

## Key Claims

- Never put actual connection strings directly into binding configuration — use application setting names.
- Azure Files does not support managed identity for file share access (Consumption/Elastic Premium plans must use connection strings).
- Identity-based connections are the preferred security pattern over secret-based connections where supported.
- Apply principle of least privilege when assigning roles/permissions.

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – entity
- [[managed-identity]] – concept
- [[application-settings]] – concept (cross-reference with LP1)
- [[create-triggers-and-bindings]] – previous source
- [[exercise-create-function-visual-studio-code]] – next source
