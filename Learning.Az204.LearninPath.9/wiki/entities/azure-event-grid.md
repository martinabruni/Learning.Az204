---
title: "Azure Event Grid"
type: entity
tags: [azure, event-grid, pub-sub, messaging, serverless, az204]
sources: [event-grid-overview.md, event-grid-schema.md, event-grid-delivery-retry.md, event-grid-access-control.md, event-grid-webhook-delivery.md, event-grid-filtering.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Event Grid

**Azure Event Grid** is a fully managed, highly scalable **Pub/Sub message distribution service** on Azure. It distributes events from sources (publishers) to handlers (subscribers) using HTTP and MQTT protocols.

## Key Facts

| Property | Value |
|----------|-------|
| Type | Fully managed PaaS |
| Protocols | HTTP, MQTT v3.1.1, v5.0 |
| Schema standards | Event Grid schema, CloudEvents 1.0 |
| Max event size | 1 MB |
| Billing increment | 64 KB |
| Default delivery attempts | 30 |
| Default event TTL | 1440 minutes (24 hours) |

## Delivery Modes

- **Push delivery**: Event Grid sends events to subscriber endpoints.
- **Pull delivery**: Subscribers connect to Event Grid to read events.

## Topic Types

- **System topics**: built-in Azure service topics.
- **Custom topics**: application or third-party topics.
- **Partner topics**: events from external partner organizations.

## Event Handlers

- Azure Logic Apps, Azure Automation, Azure Functions (auto-validated for webhooks).
- Custom webhooks (require validation handshake).
- Azure Storage Queue, Azure Event Hubs, Service Bus.

## RBAC Roles

| Role | Permission |
|------|------------|
| Event Grid Subscription Reader | Read subscriptions |
| Event Grid Subscription Contributor | Manage subscriptions |
| Event Grid Contributor | Create/manage resources |
| Event Grid Data Sender | Publish events |

## Retry and Durability

- Exponential backoff retry policy.
- Dead-letter support (requires explicit storage account configuration).
- Output batching configurable per subscription (1–5,000 events per batch).

## Related Pages

- [[event-grid-overview]] — core concepts and components
- [[event-grid-schema]] — event schema details
- [[event-grid-delivery-retry]] — delivery durability and retry policy
- [[event-grid-access-control]] — RBAC and permissions
- [[event-grid-webhook-delivery]] — webhook validation
- [[event-grid-filtering]] — subscription filters
- [[cloudevents-spec]] — CloudEvents 1.0
- [[pub-sub-pattern]] — messaging pattern
