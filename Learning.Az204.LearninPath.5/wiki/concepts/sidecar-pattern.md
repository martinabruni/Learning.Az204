---
title: "Sidecar Pattern"
type: concept
tags: [sidecar, microservices, containers, pattern, az204]
sources: [aca-containers.md, aci-overview.md, aca-authentication.md]
created: 2026-06-16
updated: 2026-06-16
---

# Sidecar Pattern

The sidecar pattern involves deploying a **helper container alongside a primary application container** within the same pod/group. The sidecar shares resources (disk, network) and lifecycle with the primary container.

## Use Cases

- **Logging agent**: reads logs from primary container on a shared volume and forwards to a logging service.
- **Cache refresher**: background process that refreshes a cache used by the primary container.
- **Auth middleware**: in ACA, the built-in auth module runs as a sidecar on each replica.
- **Monitoring/health check**: periodically verifies the primary app is responding.
- **Content sync**: pulls latest content from source control alongside a web server.

## Implementation in ACI

In [[azure-container-instances]], sidecar containers are part of a [[container-group]]. The group shares lifecycle, network (same IP), and volumes.

## Implementation in ACA

In [[azure-container-apps]], define multiple containers in the `containers` array of the ARM template. They share hard disk, network, and application lifecycle.

> Note: For microservice architectures, prefer deploying each service as a **separate container app** rather than using sidecars.

## ACA Auth Sidecar

ACA's authentication middleware runs as a sidecar on each replica — isolated from application code, no direct language/framework integration.

## Related Pages

- [[container-group]] – ACI concept
- [[azure-container-apps]] – entity page
- [[aca-containers]] – source page
- [[aca-authentication]] – auth sidecar source
