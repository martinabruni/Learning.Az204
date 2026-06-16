---
title: "Discover the API Management Service"
type: source
tags: [api-management, azure, apim, gateway, policies, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover the API Management Service

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf

## Overview

[[azure-api-management]] is a fully managed Azure service that provides the core functionality for a successful API program: developer engagement, business insights, analytics, security, and protection.

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf
> "API Management provides the core functionality to ensure a successful API program through developer engagement, business insights, analytics, security, and protection."

## Key Claims

- Each API consists of one or more operations; each API can be added to one or more [[apim-products|products]].
- Developers subscribe to a product to consume APIs; usage is subject to any configured [[apim-policies|policies]].
- API Management is available in various tiers differing in capacity and features.

## API Management Components

Three main components, all Azure-hosted and fully managed by default:

### API Gateway

The endpoint that:
- Accepts API calls and routes them to appropriate backends
- Verifies API keys and other credentials
- Enforces usage quotas and rate limits
- Transforms requests and responses via [[apim-policies|policy statements]]
- Caches responses to improve latency and reduce backend load
- Emits logs, metrics, and traces for monitoring

### Management Plane

Administrative interface used to:
- Provision and configure API Management service settings
- Define or import API schema
- Package APIs into [[apim-products|products]]
- Set up policies (quotas, transformations)
- Access analytics and insights

### Developer Portal

Automatically generated, fully customizable website where developers can:
- Read API documentation
- Call APIs via an interactive console
- Create accounts and subscribe to get API keys
- Access analytics on their own usage
- Download API definitions
- Manage API keys

## Products

- Products surface APIs to developers.
- Each product has one or more APIs, a title, description, and terms of use.
- **Open** products: usable without a subscription.
- **Protected** products: require a subscription before use.
- Subscription approval is configured at the product level: administrator approval or auto-approved.

## Groups

Three immutable system groups manage product visibility:

| Group | Description |
|-------|-------------|
| Administrators | Manage service instances, create APIs/operations/products; Azure subscription admins are members |
| Developers | Authenticated developer portal users who build apps using APIs |
| Guests | Unauthenticated users; can receive read-only access (view APIs but not call them) |

Administrators can also create custom groups or use external groups from Microsoft Entra tenants.

## Developers

- Represent user accounts in an API Management service instance.
- Can be created/invited by administrators or self-sign-up via the developer portal.
- Each developer belongs to one or more groups and can subscribe to products visible to those groups.

## Policies

- Collection of statements executed sequentially on the request or response of an API.
- Applied inside the gateway.
- Popular uses: format conversion (XML to JSON), call rate limiting.
- Policy expressions can be used as attribute values or text values.
- Applicable at four scopes: **global** (all APIs), **product**, **specific API**, **API operation**.

## Related Pages

- [[azure-api-management]] – entity page
- [[apim-gateway]] – API gateway deep dive
- [[apim-policies]] – policy configuration and expressions
- [[apim-products]] – product and subscription model
- [[apim-subscriptions]] – subscription keys and security
- [[apim-certificates]] – certificate-based authentication
