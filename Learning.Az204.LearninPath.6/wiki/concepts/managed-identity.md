---
title: "Managed Identity"
type: concept
tags: [managed-identity, entra-id, service-principal, azure, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Managed Identity

## What It Is

A managed identity is a type of [[service-principals|service principal]] in [[microsoft-entra-id]] that provides an identity for applications to use when connecting to resources that support Microsoft Entra authentication — without managing credentials in code.

## Key Properties

- When a managed identity is enabled on an Azure resource, a **service principal representing that managed identity** is automatically created in the tenant.
- The service principal **can be granted access and permissions** to other Azure resources.
- The service principal **cannot be updated or modified directly** — it is managed by the Azure platform.

## Why Use Managed Identities

- Eliminates the need to store credentials (secrets, certificates) in application code or configuration.
- Credentials are managed and rotated automatically by Azure.
- Supported by most Azure services that support Entra authentication (e.g., Key Vault, Storage, SQL).

## Related Pages

- [[service-principals]] – managed identity is one of the three SP types
- [[microsoft-entra-id]] – the identity provider hosting managed identity SPs
- [[explore-service-principals]] – source page
