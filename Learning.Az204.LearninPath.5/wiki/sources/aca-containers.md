---
title: "Explore Containers in Azure Container Apps"
type: source
tags: [container-apps, aca, sidecar, container-registries, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_4-container-apps-containers.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Containers in Azure Container Apps

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_4-container-apps-containers.pdf

## Overview

[[azure-container-apps]] abstracts Kubernetes and container orchestration. Containers can use **any runtime, programming language, or development stack**.

## Key Claims

- ACA supports any **Linux-based x86-64** (`linux/amd64`) container image.
- No required base container image.
- If a container crashes, it **automatically restarts**.
- Containers are grouped into pods inside **revision snapshots**.

## ARM Template Configuration

Changes to the ARM template `configuration` section trigger a **new container app revision**. Key fields in the `containers` array:

- `name`, `image`: container identity
- `env`: environment variables (plain or `secretRef`)
- `resources`: `cpu` and `memory` limits
- `volumeMounts`: paths and volume names
- `probes`: liveness, readiness, startup probes (HTTP or gRPC)

Example:
```json
{
  "name": "main",
  "image": "[parameters('container_image')]",
  "resources": { "cpu": 0.5, "memory": "1Gi" }
}
```

## Multiple Containers (Sidecar Pattern)

- Multiple containers in one container app share **hard disk, network resources, and application lifecycle**.
- Examples of sidecar containers:
  - Log agent reading from primary container on shared volume → forwards to logging service.
  - Background process refreshing a cache used by the primary container.

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_4-container-apps-containers.pdf
> "Running multiple containers in a single container app is an advanced use case. In most situations where you want to run multiple containers, such as when implementing a microservice architecture, deploy each service as a separate container app."

## Container Registries

- Private registries are supported via credentials in ACA configuration.
- Registry credentials are defined in the `registries` array (`properties.configuration`).
- `passwordSecretRef` references a secret by name for the registry password.

```json
{
  "registries": [{
    "server": "docker.io",
    "username": "my-registry-user-name",
    "passwordSecretRef": "my-password-secret-name"
  }]
}
```

## Limitations

| Limitation | Detail |
|---|---|
| Privileged containers | Not supported; root-access processes cause runtime errors |
| Operating system | Linux-based (`linux/amd64`) images only |

## Related Pages

- [[azure-container-apps]] – entity page
- [[sidecar-pattern]] – concept page
- [[aca-explore]] – ACA overview source
- [[aca-revisions-secrets]] – revisions and secrets source
