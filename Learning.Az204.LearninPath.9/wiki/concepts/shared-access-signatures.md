---
title: "Shared Access Signatures (SAS)"
type: concept
tags: [security, sas, event-hubs, authorization, az204]
sources: [event-hubs-access-control.md]
created: 2026-06-16
updated: 2026-06-16
---

# Shared Access Signatures (SAS)

**Shared Access Signatures (SAS)** provide delegated access to Azure resources with fine-grained control over permissions, scope, and expiry — without sharing the account key.

## SAS in Azure Event Hubs

### For Publishers (Producers)

- Each event publisher is a **virtual endpoint** for sending only.
- Each client receives a **unique SAS token** signed with a shared access key.
- A client with a token can only send to **one publisher**.
- Clients do not know the signing key (cannot forge tokens).
- Tokens expire and must be refreshed.

### For Consumers

- Consumer applications need **manage rights** or **listen privileges**.
- Rights are assigned at the **namespace level** or **event hub/topic level** (not per consumer group).
- All consumer groups of an entity share the same SAS-defined privileges.

## Contrast with Entra ID (RBAC)

| Aspect | SAS | Microsoft Entra ID / RBAC |
|--------|-----|--------------------------|
| Credential storage | Token in client | OAuth token (no stored creds) |
| Granularity | Entity-level | Role-level (RBAC) |
| Expiry | Token-based | Token-based (OAuth) |
| Recommended for | Legacy / fine-grained publisher control | Modern apps, managed identities |

## Related Pages

- [[azure-event-hubs]] — entity
- [[event-hubs-access-control]] — source page
- [[microsoft-entra-id]] — alternative auth method
- [[azure-rbac]] — role-based access control
