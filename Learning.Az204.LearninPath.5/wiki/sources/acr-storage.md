---
title: "Explore ACR Storage Capabilities"
type: source
tags: [acr, storage, geo-replication, encryption, az204]
sources: [learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_3-azure-container-registry-storage.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore ACR Storage Capabilities

> [!source] learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_3-azure-container-registry-storage.pdf

## Overview

All [[azure-container-registry]] tiers benefit from advanced Azure storage features.

## Storage Features

### Encryption-at-Rest

- All images and artifacts are **encrypted at rest** automatically.
- Azure encrypts before storing and decrypts on-the-fly during pulls.
- Optionally add an extra layer with a **customer-managed key**.

### Regional Storage

- Registry data is stored in the **region where the registry is created** (data residency and compliance).
- In most regions, data may also be stored in a **paired region** in the same geography.
- **Brazil South and Southeast Asia**: data is always confined to the region.
- Regional outage: data may become unavailable and is **not automatically recovered** — enable geo-replication for resilience.

### Geo-Replication (Premium only)

- Protects against regional failure.
- Provides **network-close image storage** for faster pushes/pulls in distributed development.

### Zone Redundancy (Premium only)

- Uses **Azure Availability Zones** to replicate registry to a minimum of **three separate zones** per enabled region.

### Scalable Storage

- Create as many repositories, images, layers, and tags as needed (up to registry storage limit).
- High numbers of repositories/tags can **impact registry performance** — periodically delete unused resources.
- **Deleted resources cannot be recovered** (repositories, images, tags).

## Related Pages

- [[azure-container-registry]] – entity page
- [[acr-overview]] – ACR overview source
- [[acr-tasks]] – ACR Tasks source
