---
title: "Managed Identity"
type: concept
tags: [managed-identity, security, azure-functions, rbac, identity, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_4-connect-azure-services.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Managed Identity

## Definition

**Managed Identity** is an Azure AD identity automatically managed by Azure that enables services (like [[azure-functions]]) to authenticate to other Azure services without storing credentials in code or configuration.

## Types

| Type | Description |
|------|-------------|
| System-assigned | Created with the resource; lifecycle tied to the resource |
| User-assigned | Created independently; can be shared across resources |

## In Azure Functions

- Identity-based connections use a managed identity instead of connection strings/keys.
- **System-assigned identity** is used by default.
- **User-assigned identity**: specify via `credential` and `clientID` properties. Configuring by resource ID is **not** supported.
- During local development, the **developer identity** is used instead of a managed identity.

## Granting Permissions

Permissions must be explicitly granted:
- Assign a role in **Azure RBAC** (role-based access control), or
- Specify the identity in a **service-specific access policy**.

Apply the **principle of least privilege**: grant only the permissions required for the intended action.

## Limitations

- Azure Files does **not** support managed identity for file share access. Consumption and Elastic Premium plans must use `WEBSITE_AZUREFILESCONNECTIONSTRING` and `WEBSITE_CONTENTSHARE` connection string settings.
- Not all extensions/services support identity-based connections; check extension documentation.

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – entity
- [[connect-functions-to-azure-services]] – source
- [[application-settings]] – environment variable configuration (cross-reference LP1)
