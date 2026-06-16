---
title: "Explore Dapr Integration with Azure Container Apps"
type: source
tags: [container-apps, aca, dapr, microservices, pub-sub, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_7-explore-distributed-application-runtime.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Dapr Integration with Azure Container Apps

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_7-explore-distributed-application-runtime.pdf

## Overview

[[dapr]] (Distributed Application Runtime) is a set of incrementally adoptable features that simplify authoring distributed, microservice-based applications.

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_7-explore-distributed-application-runtime.pdf
> "Dapr provides capabilities for enabling application intercommunication through messaging via pub/sub or reliable and secure service-to-service calls."

## Key Claims

- Dapr is open source and a **CNCF** (Cloud Native Computing Foundation) project under the Linux Foundation.
- [[azure-container-apps]] provides a **managed, supported Dapr integration** — no need to manage Dapr OSS yourself.
- ACA handles **Dapr version upgrades** seamlessly.
- Dapr sidecar runs on **HTTP port 3500** and **gRPC port 50001**.

## Dapr APIs

| API | Description |
|---|---|
| Service-to-service invocation | Direct service calls with automatic mTLS authentication and encryption |
| State management | Transactions and CRUD operations for stateful services |
| Pub/sub | Publisher/subscriber communication via message broker |
| Bindings | Trigger applications based on events (input/output) |
| Actors | Message-driven, single-threaded units of work for burst-heavy workloads |
| Observability | Send tracing to Application Insights backend |
| Secrets | Access secrets from application code or Dapr components |
| Configuration | Retrieve and subscribe to application configuration items |

## Dapr Core Concepts (Pub/Sub Example)

1. **Container Apps with Dapr enabled**: Dapr arguments are set at the container app level and apply to all revisions.
2. **Dapr sidecar**: Managed Dapr APIs are exposed to each container app via a sidecar, invokable via HTTP or gRPC.
3. **Dapr component configuration**: Modular design — components can be shared across apps or scoped via the `scopes` array.

## Dapr Enablement Channels

- Container Apps CLI
- IaC templates (Bicep or ARM)
- Azure portal

## Dapr Components and Scopes

- Components are **environment-level resources**.
- Can be shared across apps or **scoped** to specific container apps.
- Can use Dapr secrets for secure configuration metadata.
- By default, all Dapr-enabled apps in an environment load **all deployed components** — use scopes to restrict.

## Related Pages

- [[dapr]] – entity page
- [[azure-container-apps]] – entity page
- [[pub-sub-pattern]] – concept page
- [[aca-explore]] – ACA overview source
