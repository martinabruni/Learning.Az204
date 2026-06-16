---
title: "Microsoft Entra ID"
type: entity
tags: [security, identity, oauth, azure, az204]
sources: [event-hubs-access-control.md]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Entra ID

**Microsoft Entra ID** (formerly Azure Active Directory) is Microsoft's cloud-based identity and access management platform. It provides authentication and authorization for Azure services using industry-standard protocols.

## Role in Event Hubs

[[azure-event-hubs]] supports Microsoft Entra ID as a first-class authorization mechanism via OAuth 2.0.

Key advantage over SAS: **credentials are not stored in application code**. Instead:

1. Application requests an OAuth 2.0 access token from Microsoft identity platform.
2. Entra ID authenticates the security principal (user, group, or service principal).
3. On success, returns an access token.
4. Application uses the token for authorized requests.

## RBAC Integration

Entra ID works with Azure RBAC to assign roles to:
- Users
- Groups
- Service principals
- Managed identities

## Related Pages

- [[azure-event-hubs]] — Event Hubs entity
- [[azure-event-grid]] — Event Grid entity
- [[azure-rbac]] — RBAC concept
- [[shared-access-signatures]] — alternative auth method
