---
title: "Event Grid Security and Access Control"
type: concept
tags: [event-grid, security, rbac, permissions, az204]
sources: [event-grid-access-control.md, event-grid-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Event Grid Security and Access Control

[[azure-event-grid]] uses **Azure RBAC** to control access to management operations and event publishing.

## Built-in Roles

| Role | Scope | Key Use |
|------|-------|---------|
| Event Grid Subscription Reader | Subscriptions | Read subscriptions (needed for event domains) |
| Event Grid Subscription Contributor | Subscriptions | Manage subscriptions (needed for event domains) |
| Event Grid Contributor | Resources | Create and manage Event Grid resources |
| Event Grid Data Sender | Topics | Publish events |

## Permission for Writing Event Subscriptions

When using non-WebHook handlers, you need `Microsoft.EventGrid/EventSubscriptions/Write` on the event source:

| Topic Type | Permission Scope |
|------------|-----------------|
| System topics | Scope of the Azure resource publishing events |
| Custom topics | Scope of the Event Grid custom topic resource |

## Managed Identity for Push Delivery

When using push delivery with managed identity as the event handler identity, the managed identity must have an appropriate RBAC role on the target resource (e.g., **Event Hubs Data Sender** to send to an event hub).

## Related Pages

- [[azure-event-grid]] — entity
- [[event-grid-access-control]] — source page
- [[azure-rbac]] — RBAC concept
- [[webhook-validation-pattern]] — webhook security
