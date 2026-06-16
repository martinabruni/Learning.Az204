---
title: "Control Access to Events (Event Grid)"
type: source
tags: [event-grid, rbac, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_5-authorize-access-event-grid.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Control Access to Events (Event Grid)

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_5-authorize-access-event-grid.pdf

## Overview

[[azure-event-grid]] uses **Azure RBAC** to control access for management operations: listing event subscriptions, creating new ones, and generating keys.

## Built-in Roles

| Role | Description |
|------|-------------|
| Event Grid Subscription Reader | Read Event Grid event subscriptions |
| Event Grid Subscription Contributor | Manage event subscription operations |
| Event Grid Contributor | Create and manage Event Grid resources |
| Event Grid Data Sender | Send events to Event Grid topics |

- **Subscription Reader / Contributor**: focused on subscriptions; do not grant access for creating topics.
- **Contributor**: create and manage resources.
- **Data Sender**: publish events to topics.

## Permissions for Event Subscriptions

Required permission: `Microsoft.EventGrid/EventSubscriptions/Write` on the event source resource.

This applies when using a non-WebHook handler (e.g., event hub, queue storage).

### Permission Scope

| Topic Type | Required Scope Format |
|------------|-----------------------|
| System topics | `/subscriptions/{id}/resourceGroups/{rg}/providers/{provider}/{type}/{name}` |
| Custom topics | `/subscriptions/{id}/resourceGroups/{rg}/providers/Microsoft.EventGrid/topics/{name}` |

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-overview]] — core concepts
- [[azure-rbac]] — Azure RBAC concept
- [[event-grid-security]] — security concept page
