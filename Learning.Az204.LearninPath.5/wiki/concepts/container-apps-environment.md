---
title: "Container Apps Environment"
type: concept
tags: [container-apps, aca, environment, virtual-network, az204]
sources: [aca-explore.md]
created: 2026-06-16
updated: 2026-06-16
---

# Container Apps Environment

A Container Apps Environment is a **secure boundary** around groups of [[azure-container-apps]] container apps. It is the deployment target for individual container apps.

## Shared Resources

Apps in the same environment share:
- The same **Virtual Network**
- The same **Log Analytics workspace**

## When to Use the Same Environment

- Managing related services
- Deploying to the same VNet
- Using Dapr with shared service invocation API
- Sharing Dapr configuration
- Sharing log analytics workspace

## When to Use Different Environments

- Ensuring compute isolation between apps
- Preventing Dapr service-to-service communication between apps

## VNet Integration

An existing virtual network can be provided at environment creation time.

## Related Pages

- [[azure-container-apps]] – entity page
- [[aca-explore]] – source page
- [[dapr]] – Dapr integration entity
