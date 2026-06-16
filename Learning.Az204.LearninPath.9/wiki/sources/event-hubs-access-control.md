---
title: "Control Access to Events (Event Hubs)"
type: source
tags: [event-hubs, security, rbac, sas, entra-id, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-hubs_5-event-hubs-authentication-authorization.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Control Access to Events (Event Hubs)

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-hubs_5-event-hubs-authentication-authorization.pdf

## Overview

[[azure-event-hubs]] supports both **Microsoft Entra ID** and **Shared Access Signatures (SAS)** for authentication and authorization.

## Built-in Azure Roles (Entra ID / RBAC)

| Role | Description |
|------|-------------|
| Azure Event Hubs Data Owner | Complete access to Event Hubs resources |
| Azure Event Hubs Data Sender | Send access to Event Hubs resources |
| Azure Event Hubs Data Receiver | Receiving access to Event Hubs resources |

## Authorize with Managed Identities

Configure Azure RBAC for the managed identity. When an Azure role is assigned to a managed identity, it is granted access at the appropriate scope.

## Authorize with Microsoft Identity Platform (Entra ID + OAuth)

Key advantage: credentials not stored in code. Workflow:

1. Application requests an **OAuth 2.0 access token** from Microsoft identity platform.
2. Entra ID authenticates the security principal (user, group, or service principal).
3. On success, Entra ID returns an access token.
4. Application uses the token to authorize requests to Event Hubs.

## Authorize Publishers with SAS

- An **event publisher** defines a virtual endpoint for sending only (cannot receive).
- Typically one publisher per client.
- Each client is assigned a **unique token** signed with a shared access signature key.
- A client with a token can only send to one publisher.
- Clients do not know the key; cannot manufacture tokens.
- Tokens expire and must be refreshed.

## Authorize Consumers with SAS

- Back-end consumer applications require either **manage rights** or **listen privileges** at the namespace or event hub level.
- SAS policy scope is at the **entity level** (namespace or event hub), not at the consumer group level.
- Privileges defined at namespace level apply to all consumer groups of that entity.

## Related Pages

- [[azure-event-hubs]] — entity page
- [[event-hubs-overview]] — overview
- [[azure-rbac]] — RBAC concept
- [[shared-access-signatures]] — SAS concept
- [[microsoft-entra-id]] — identity platform entity
