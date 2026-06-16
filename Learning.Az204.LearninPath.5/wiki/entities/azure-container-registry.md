---
title: "Azure Container Registry (ACR)"
type: entity
tags: [acr, container-registry, docker, az204]
sources: [acr-overview.md, acr-storage.md, acr-tasks.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Container Registry (ACR)

Azure Container Registry is a **managed private container registry service** based on open-source Docker Registry 2.0. It stores, manages, and secures container images and artifacts.

## Key Attributes

| Attribute | Value |
|---|---|
| Type | Managed private container registry |
| Based on | Docker Registry 2.0 (open source) |
| Supported formats | Docker images, Helm charts, OCI images |
| Security | Encryption-at-rest, Microsoft Entra auth, private endpoints (Premium) |

## Service Tiers

| Tier | Best for |
|---|---|
| Basic | Dev/learning; lower storage and throughput |
| Standard | Most production scenarios |
| Premium | High-volume; adds geo-replication, content trust, private link, zone redundancy |

## Storage Features

- Encryption-at-rest (all tiers; optional customer-managed key)
- Regional storage with data residency compliance
- Geo-replication (Premium): resilience and network-close pulls
- Zone redundancy (Premium): replication across ≥3 availability zones
- Scalable storage: unlimited repos/images/tags (up to storage limit); deleted resources are unrecoverable

## ACR Tasks

[[acr-tasks-concept]] automates: quick builds, source-code-triggered builds, base-image-update-triggered builds, scheduled builds, and multi-step YAML workflows.

## Source Pages

- [[acr-overview]] – overview and service tiers
- [[acr-storage]] – storage capabilities
- [[acr-tasks]] – task scenarios and image platforms
- [[dockerfile-components]] – Dockerfile reference
