---
title: "API Management Gateway"
type: concept
tags: [api-management, gateway, reverse-proxy, data-plane, runtime, hybrid, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-api-management_3-api-gateways.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# API Management Gateway

## Definition

The API Management gateway (also called **data plane** or **runtime**) is the service component responsible for proxying API requests, applying policies, and collecting telemetry. It sits between clients and backend services, acting as a **reverse proxy**.

## Responsibilities

- Accept API calls and route them to appropriate backends
- Verify API keys and other credentials
- Enforce usage quotas and rate limits
- Transform requests and responses via [[apim-policies|policy statements]]
- Cache responses to improve latency and reduce backend load
- Emit logs, metrics, and traces for monitoring, reporting, and troubleshooting
- Handle SSL termination and authentication

## Why a Gateway is Needed

Without a gateway, direct service exposure causes:
- Complex client code (must track multiple endpoints)
- Tight client-backend coupling
- Fan-out calls (one operation calls multiple services)
- Each service must implement cross-cutting concerns independently
- Limited protocol choices (must be HTTP/WebSocket)
- Larger attack surface

## Gateway Variants

### Managed Gateway

- Default, deployed in Azure for every APIM instance in every service tier.
- All traffic flows through Azure regardless of backend location.

### Self-Hosted Gateway

- Optional, containerized version of the managed gateway.
- Used in **hybrid** and **multicloud** scenarios.
- Runs on-premises or in other clouds, co-located with backends.
- Still managed centrally from a single [[azure-api-management]] service in Azure.

## Related Pages

- [[azure-api-management]] – parent service
- [[apim-policies]] – policies applied by the gateway
- [[apim-subscriptions]] – subscription keys validated by the gateway
- [[apim-certificates]] – TLS mutual auth enforced at the gateway
- [[api-gateways]] – source page
- [[api-management-overview]] – service overview
