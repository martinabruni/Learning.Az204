---
title: "Azure Role-Based Access Control (RBAC)"
type: concept
tags: [security, rbac, azure, authorization, az204]
sources: [event-grid-access-control.md, event-hubs-access-control.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Role-Based Access Control (RBAC)

**Azure RBAC** is the authorization system for managing access to Azure resources. It allows granting specific permissions to users, groups, service principals, and managed identities at different scopes.

## Core Concepts

| Concept | Description |
|---------|-------------|
| Role definition | A collection of permissions (e.g., "read", "write") |
| Security principal | User, group, service principal, or managed identity |
| Scope | Resource, resource group, subscription, or management group |
| Role assignment | Binds a role definition to a security principal at a scope |

## Event Grid Built-in Roles

| Role | Purpose |
|------|---------|
| Event Grid Subscription Reader | Read subscriptions |
| Event Grid Subscription Contributor | Manage subscriptions |
| Event Grid Contributor | Create and manage resources |
| Event Grid Data Sender | Send events to topics |

## Event Hubs Built-in Roles

| Role | Purpose |
|------|---------|
| Azure Event Hubs Data Owner | Full access |
| Azure Event Hubs Data Sender | Send only |
| Azure Event Hubs Data Receiver | Receive only |

## Related Pages

- [[azure-event-grid]] — Event Grid RBAC usage
- [[azure-event-hubs]] — Event Hubs RBAC usage
- [[event-grid-security]] — Event Grid security concept
- [[shared-access-signatures]] — alternative auth mechanism
- [[microsoft-entra-id]] — identity provider for RBAC
