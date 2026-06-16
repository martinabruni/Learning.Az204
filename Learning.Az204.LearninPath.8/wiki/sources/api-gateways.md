---
title: "Explore API Gateways"
type: source
tags: [api-management, gateway, reverse-proxy, hybrid, self-hosted, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_3-api-gateways.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore API Gateways

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_3-api-gateways.pdf

## Overview

The [[apim-gateway|API Management gateway]] (also called **data plane** or **runtime**) is responsible for proxying API requests, applying policies, and collecting telemetry.

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_3-api-gateways.pdf
> "The API Management gateway (also called data plane or runtime) is the service component that's responsible for proxying API requests, applying policies, and collecting telemetry."

## Key Claims

- A gateway sits between clients and services, acting as a **reverse proxy**.
- Without a gateway, clients must call backend services directly, introducing serious problems.
- The gateway decouples clients from services.

## Problems with Direct Service Exposure

| Problem | Description |
|---------|-------------|
| Complex client code | Client must track multiple endpoints and handle failures resiliently |
| Client-backend coupling | Client needs to know how services are decomposed; harder to maintain or refactor |
| Fan-out calls | A single operation may require calls to multiple services |
| Cross-cutting concerns | Each service must handle auth, SSL, and rate limiting individually |
| Protocol constraints | Services must expose HTTP/WebSocket; limits protocol choice |
| Attack surface | Public-facing services must be hardened individually |

## Gateway Capabilities

The gateway performs cross-cutting tasks including:
- Authentication and credential verification
- SSL termination
- Rate limiting and quota enforcement
- Request/response transformation
- Response caching
- Telemetry collection (logs, metrics, traces)

## Managed and Self-Hosted Gateways

[[azure-api-management]] offers two gateway deployment modes:

### Managed Gateway

- Default gateway component deployed in Azure for every API Management instance in every service tier.
- All API traffic flows through Azure regardless of where backend services are hosted.

### Self-Hosted Gateway

- Optional, **containerized** version of the default managed gateway.
- Useful for **hybrid** and **multicloud** scenarios.
- Allows running the gateway off Azure, in the same environments where API backends are hosted.
- Enables managing on-premises and cross-cloud APIs from a single API Management service in Azure.

## Related Pages

- [[azure-api-management]] – parent service entity
- [[apim-gateway]] – gateway concept page
- [[api-management-overview]] – API Management service overview
- [[apim-policies]] – policies applied by the gateway
