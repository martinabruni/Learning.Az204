---
title: "Dapr (Distributed Application Runtime)"
type: entity
tags: [dapr, microservices, pub-sub, service-invocation, cncf, az204]
sources: [aca-dapr.md, aca-explore.md]
created: 2026-06-16
updated: 2026-06-16
---

# Dapr (Distributed Application Runtime)

Dapr is an **open-source, CNCF project** that provides incrementally adoptable building blocks for developing distributed, microservice-based applications.

## Key Attributes

| Attribute | Value |
|---|---|
| Type | Open-source distributed systems runtime |
| Governance | CNCF (Cloud Native Computing Foundation) / Linux Foundation |
| Integration with ACA | Managed, supported — no OSS self-management needed |
| Sidecar port (HTTP) | 3500 |
| Sidecar port (gRPC) | 50001 |

## Dapr APIs

| API | Purpose |
|---|---|
| Service-to-service invocation | Reliable calls with automatic mTLS |
| State management | Transactions and CRUD for stateful services |
| Pub/sub | Messaging via intermediary broker |
| Bindings | Event-triggered input/output |
| Actors | Single-threaded, message-driven units for burst workloads |
| Observability | Tracing to Application Insights |
| Secrets | Secure secret access |
| Configuration | Subscribe to config store changes |

## How Dapr Works in ACA

1. Dapr is **enabled at the container app level** (applies to all revisions in multi-revision mode).
2. Dapr APIs are exposed via a **sidecar** per container app.
3. **Components** (e.g., pub/sub, state stores) are environment-level, shareable, and can be scoped to specific apps.

## Related Pages

- [[azure-container-apps]] – the platform that hosts Dapr-enabled apps
- [[aca-dapr]] – source page with full API list and concepts
- [[pub-sub-pattern]] – concept page
