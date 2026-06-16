---
title: "API Management Products"
type: concept
tags: [api-management, products, subscriptions, access-control, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_2-api-management-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-api-management_6-secure-access-api-subscriptions.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# API Management Products

## Definition

Products are the mechanism for surfacing APIs to developers in [[azure-api-management]]. A product bundles one or more APIs and defines the terms under which they are consumed.

## Product Properties

- **Title**, **description**, and **terms of use**
- One or more APIs (an API can belong to multiple products)
- **Open** or **Protected** access model
- Subscription approval setting: administrator approval or auto-approved

## Open vs Protected Products

| Type | Subscription Required | Use Case |
|------|--------------------|----------|
| Open | No | Public APIs, free tier, documentation APIs |
| Protected | Yes | Commercial APIs, partner APIs, rate-limited tiers |

## Products and Subscription Scopes

When subscriptions are enabled on a product, clients must supply a subscription key to call any API in that product. Subscription keys can be scoped to:

- **All APIs** – gateway-wide
- **Single API** – one imported API and all its endpoints
- **Product** – all APIs in the product, with the product's access rules and quotas

## Products and Groups

[[apim-groups|Groups]] control which developers can see which products:
- **Administrators** can see all products.
- **Developers** see products that have their group assigned.
- **Guests** have limited visibility (read-only if configured).

## Relationship to Policies

Policies can be scoped to a product, applying to all APIs within it. This allows product-level rate limiting, quotas, and content filtering.

## Related Pages

- [[azure-api-management]] – parent service
- [[apim-subscriptions]] – subscription keys linked to products
- [[apim-policies]] – product-scoped policies
- [[apim-gateway]] – enforces product-level access rules
- [[api-management-overview]] – source covering products and groups
- [[secure-access-api-subscriptions]] – source covering subscription scopes
