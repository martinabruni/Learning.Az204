---
title: "Explore Service Principals"
type: source
tags: [service-principal, app-registration, entra-id, managed-identity, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Service Principals

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf

## Overview

To delegate Identity and Access Management (IAM) functions to [[microsoft-entra-id]], an application must be registered with a Microsoft Entra tenant. Registration creates an identity configuration — an application object and a [[service-principals|service principal object]] — in the home tenant.

## Key Claims

### Application Registration

- When registering in the Azure portal, you choose: **Single tenant** (only accessible in your tenant) or **Multi-tenant** (accessible in other tenants).
- Registration creates:
  - An **application object** — the globally unique instance of the app (lives in the home tenant).
  - A **service principal object** — automatically created in the home tenant.
  - A globally unique **app/client ID** (GUID).
- Service principal objects can also be created programmatically via Azure PowerShell, Azure CLI, Microsoft Graph, etc.

### Application Object

- Scoped to its one and only application object in its home tenant.
- Serves as a **template or blueprint** to create one or more service principal objects (analogous to a class in OOP).
- Describes three aspects of an application:
  1. How the service can issue tokens to access the application.
  2. Resources the application might need to access.
  3. Actions the application can take.
- Schema defined by the **Microsoft Graph Application entity**.

### Service Principal Object

- The **security principal** defines access policy and permissions for a user/application in a tenant.
- Enables authentication during sign-in and authorization during resource access.
- Three types of service principal:
  1. **Application** — local representation of a global app object in a single tenant. Created in each tenant where the app is used.
  2. **Managed identity** — represents a managed identity; created automatically when a managed identity is enabled. Cannot be updated or modified directly.
  3. **Legacy** — apps created before app registrations existed; has credentials, service principal names, reply URLs, but no associated app registration.

### Relationship: Application Object vs Service Principal

> [!source] learn.microsoft.com_en-us_training_modules_explore-microsoft-identity-platform_3-app-service-principals.pdf
> "The application object is the global representation of your application for use across all tenants, and the service principal is the local representation for use in a specific tenant."

- Application object: **1-to-1** with the software application; **1-to-many** with service principal objects.
- Single-tenant app: one service principal (home tenant only).
- Multi-tenant app: one service principal per tenant where a user consented.

## Related Pages

- [[microsoft-identity-platform]] – the broader platform
- [[microsoft-entra-id]] – identity provider and tenant host
- [[service-principals]] – concept page for service principals
- [[managed-identity]] – managed identity concept
- [[permissions-and-consent]] – consent during multi-tenant registration
