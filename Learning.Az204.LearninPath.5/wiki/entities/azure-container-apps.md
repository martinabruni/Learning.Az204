---
title: "Azure Container Apps (ACA)"
type: entity
tags: [aca, container-apps, microservices, serverless, kubernetes, az204]
sources: [aca-explore.md, aca-containers.md, aca-authentication.md, aca-revisions-secrets.md, aca-dapr.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Container Apps (ACA)

Azure Container Apps is a **fully managed serverless container service** built on top of [[azure-kubernetes-service]]. It abstracts Kubernetes complexity and is designed for microservices and event-driven workloads.

## Key Attributes

| Attribute | Value |
|---|---|
| Type | Serverless container platform (PaaS) |
| Underlying platform | Azure Kubernetes Service (AKS) |
| OS Support | Linux only (`linux/amd64`) |
| Scaling | HTTP, events (KEDA), CPU/memory; most apps scale to zero |
| Networking | Built-in HTTPS ingress, DNS-based service discovery |
| Observability | Azure Log Analytics |

## Core Concepts

- [[container-apps-environment]]: secure boundary grouping container apps; shared VNet and Log Analytics workspace
- [[container-app-revisions]]: immutable snapshots for versioning; enable traffic splitting for Blue/Green and A/B
- [[federated-identity]]: built-in EasyAuth with Microsoft, GitHub, Google, Facebook, X, OpenID Connect
- [[sidecar-pattern]]: multiple containers in one app sharing disk and network
- [[dapr]]: native integration for pub/sub, service invocation, state management, and more

## Limitations

- No privileged containers (root-access processes fail at runtime)
- Linux-only (`linux/amd64`)

## Source Pages

- [[aca-explore]] – overview and environments
- [[aca-containers]] – container configuration and sidecar pattern
- [[aca-authentication]] – built-in auth/authz
- [[aca-revisions-secrets]] – versioning and secret management
- [[aca-dapr]] – Dapr integration
