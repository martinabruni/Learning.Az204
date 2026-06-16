---
title: "Azure API Management"
type: entity
tags: [api-management, apim, azure, paas, gateway, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-api-management_3-api-gateways.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure API Management

## What It Is

Azure API Management (APIM) is a fully managed Azure service for publishing, securing, transforming, maintaining, and monitoring APIs. It provides a turnkey platform for developer engagement, business insights, analytics, security, and API protection.

## Core Components

| Component | Role |
|-----------|------|
| API Gateway | Proxies requests, enforces policies, collects telemetry |
| Management Plane | Administrative interface for configuring the service |
| Developer Portal | Auto-generated website for API documentation and self-service |

## Service Tiers

Available in multiple tiers differing in capacity and features. The **Consumption tier** is designed for serverless scenarios and requires explicit enablement of client certificates.

## Key Capabilities

- Route and transform API requests and responses
- Enforce rate limits, quotas, and authentication
- Cache responses to reduce backend load
- Emit logs, metrics, and traces for monitoring
- Support managed (Azure-hosted) and self-hosted (containerized) gateways
- Manage product catalog and developer subscriptions
- Apply XML-based policy pipelines

## Security Mechanisms

| Mechanism | Description |
|-----------|-------------|
| Subscription keys | `Ocp-Apim-Subscription-Key` header or `subscription-key` query parameter |
| OAuth 2.0 | Token-based authorization |
| Client certificates | TLS mutual authentication via inbound policies |
| IP allow listing | Restrict by source IP |

## Related Pages

- [[apim-gateway]] – API gateway (data plane)
- [[apim-policies]] – policy pipeline configuration
- [[apim-advanced-policies]] – advanced policy statements
- [[apim-products]] – product and subscription management
- [[apim-subscriptions]] – subscription keys and scopes
- [[apim-certificates]] – certificate-based authentication
- [[tls-mutual-auth]] – TLS mutual auth concept

## Source References

- [[api-management-overview]]
- [[api-gateways]]
- [[api-management-policies]]
- [[create-advanced-policies]]
- [[secure-access-api-subscriptions]]
- [[secure-access-api-certificates]]
