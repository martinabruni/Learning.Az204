---
title: "Explore Elements of a Dockerfile"
type: source
tags: [dockerfile, docker, container-images, az204]
sources: [learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_5-dockerfile-components.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Elements of a Dockerfile

> [!source] learn.microsoft.com_en-us_training_modules_publish-container-image-to-azure-container-registry_5-dockerfile-components.pdf

## Overview

A [[dockerfile]] is a script containing a series of instructions used to build a Docker image.

## Typical Dockerfile Contents

- Base or parent image
- Commands to update the base OS and install software
- Build artifacts (e.g., the compiled application)
- Services to expose (storage, network configuration)
- Command to run when the container starts

## Example Dockerfile (.NET 6)

```dockerfile
# Use the .NET 6 runtime as a base image
FROM mcr.microsoft.com/dotnet/runtime:6.0

# Set the working directory to /app
WORKDIR /app

# Copy published app to container
COPY bin/Release/net6.0/publish/ .

# Document that the application listens on port 80
EXPOSE 80

# Set the command to run when the container starts
CMD ["dotnet", "MyApp.dll"]
```

## Dockerfile Instruction Reference

| Instruction | Purpose |
|---|---|
| `FROM` | Sets the base/parent image |
| `WORKDIR` | Sets the working directory inside the container |
| `COPY` | Copies files from the build context into the container filesystem |
| `EXPOSE` | Documents the port the app listens on (does **not** publish the port) |
| `CMD` | Default command to run when the container starts |

## Key Notes

- `EXPOSE` does not publish the port to the host — use `docker run -p <host_port>:<container_port>` to publish.
- Each instruction creates a **cached container image layer** during the build.
- Final image is the composition of all layers.

## External Resources

- Docker run reference: https://docs.docker.com/engine/reference/run/
- Docker build reference: https://docs.docker.com/engine/reference/commandline/build/

## Related Pages

- [[dockerfile]] – concept page
- [[azure-container-registry]] – entity page
- [[acr-tasks]] – ACR Tasks source
- [[acr-overview]] – ACR overview source
