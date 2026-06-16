---
title: "Service Principals"
type: concept
tags: [service-principal, app-registration, entra-id, managed-identity, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Service Principals

## What It Is

A service principal is the **local representation** of an application (or managed identity) within a specific [[microsoft-entra-id]] tenant. It defines the access policy and permissions for the app in that tenant.

## Application Object vs Service Principal

| Aspect | Application Object | Service Principal |
|--------|-------------------|------------------|
| Scope | Global (home tenant only) | Local (per tenant) |
| Relationship | 1-to-1 with the software app | 1-to-many from the app object |
| Analogy | Class (OOP) | Instance (OOP) |
| Location | Home tenant | Every tenant where app is used |

## Three Types of Service Principal

1. **Application** — local instance of a multi- or single-tenant registered app. Defines what the app can do in a specific tenant, who can access it, and what resources it can access.
2. **Managed identity** — represents an Azure managed identity. Auto-created when a managed identity is enabled; cannot be updated or modified directly.
3. **Legacy** — represents apps created before the current app registration model. Has credentials, SP names, reply URLs; lacks an associated app registration.

## How Service Principals Are Created

- Automatically during app registration in the Azure portal.
- Programmatically via Azure PowerShell, Azure CLI, or Microsoft Graph.
- For multi-tenant apps: one SP is created per tenant where a user from that tenant consents.

## Related Pages

- [[microsoft-entra-id]] – the tenant that hosts service principals
- [[microsoft-identity-platform]] – the broader platform
- [[managed-identity]] – one of the SP types
- [[explore-service-principals]] – source page
