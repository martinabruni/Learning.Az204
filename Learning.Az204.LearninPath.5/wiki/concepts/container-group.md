---
title: "Container Group (ACI)"
type: concept
tags: [aci, container-group, kubernetes-pod, az204]
sources: [aci-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Container Group

A container group is the **top-level resource in [[azure-container-instances]]**. It is a collection of containers scheduled on the same host machine that share lifecycle, resources, local network, and storage volumes.

> Analogous to a **pod** in Kubernetes.

## Shared Resources

- Lifecycle (start/stop together)
- CPU and memory (sum of instance requests)
- Single public IP address and port namespace
- Storage volumes

## Networking Details

- Container groups share **one IP address** and a port namespace.
- **Port mapping is not supported** within a group.
- Containers in the group can reach each other via `localhost`.
- External exposure requires explicit port declaration on the IP.

## Deployment Formats

| Format | When to use |
|---|---|
| ARM template | When also deploying other Azure resources |
| YAML file | When deploying only container instances (more concise) |

## Multi-Container Group Limitation

- Multi-container groups: **Linux containers only**.
- Windows containers: **single instance only**.

## Common Patterns

- App + logging sidecar
- App + monitoring sidecar
- Front-end + back-end
- Web server + content-sync agent

## Related Pages

- [[azure-container-instances]] – entity page
- [[aci-overview]] – source page
- [[sidecar-pattern]] – concept page
