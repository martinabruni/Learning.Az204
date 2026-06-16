---
title: "Dockerfile"
type: concept
tags: [dockerfile, docker, container-images, az204]
sources: [dockerfile-components.md]
created: 2026-06-16
updated: 2026-06-16
---

# Dockerfile

A Dockerfile is a **text script** containing ordered instructions that Docker uses to build a container image. Each instruction creates a **cached layer** in the final image.

## Core Instructions

| Instruction | Purpose |
|---|---|
| `FROM` | Sets the base/parent image (required, first instruction) |
| `WORKDIR` | Sets the working directory inside the container |
| `COPY` | Copies files/directories from build context into the image |
| `RUN` | Executes commands during image build (e.g., install packages) |
| `EXPOSE` | Documents the port the container listens on (metadata only) |
| `ENV` | Sets environment variables |
| `CMD` | Default command to run when the container starts |
| `ENTRYPOINT` | Configures the container as an executable |

## Important Distinctions

- `EXPOSE` is **documentation only** — it does not publish the port to the host.
- To publish a port: `docker run -p <host_port>:<container_port>`
- `CMD` can be overridden at runtime; `ENTRYPOINT` is harder to override.

## Layer Caching

Each Dockerfile instruction creates a layer. Docker caches layers; if a layer hasn't changed, it reuses the cache, speeding up builds.

## ACR Tasks Integration

ACR Tasks (`az acr build`) uses a Dockerfile and a build context to build images in the cloud. See [[acr-tasks-concept]].

## Related Pages

- [[azure-container-registry]] – entity page
- [[dockerfile-components]] – source page with .NET 6 example
- [[acr-tasks-concept]] – concept page
