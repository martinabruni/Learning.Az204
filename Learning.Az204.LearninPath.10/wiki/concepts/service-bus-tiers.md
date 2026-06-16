---
title: "Service Bus Tiers"
type: concept
tags: [service-bus, tiers, pricing, az204]
sources: [azure-service-bus-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Service Bus Tiers

## Overview

[[azure-service-bus]] offers three pricing tiers designed for different use cases.

## Tier Comparison

| Feature | Basic | Standard | Premium |
|---------|-------|----------|---------|
| Throughput | Low | Variable | High |
| Performance | N/A | Variable latency | Predictable latency |
| Pricing | Pay as you go | Pay as you go (variable) | Fixed per messaging unit |
| Scaling | N/A | N/A | Scale up and down |
| Max message size | 256 KB | 256 KB | Up to 100 MB |
| Topics & Subscriptions | No | Yes | Yes |
| Transactions | No | Yes | Yes |
| Auto-forwarding | No | Yes | Yes |
| Message sessions | No | Yes | Yes |
| JMS 2.0 | No | No | Yes |

## When to Use Each Tier

- **Basic**: Simple messaging, low cost, queues only. No topics, no transactions.
- **Standard**: Dev/test environments or low-to-medium throughput scenarios not sensitive to throttling.
- **Premium**: Production workloads requiring predictable performance, high throughput, large messages, or JMS 2.0 compatibility. CPU and memory isolation at the resource level. Supports workload scaling.

## Related Pages

- [[azure-service-bus]] – entity page
- [[azure-service-bus-overview]] – source document
- [[service-bus-advanced-features]] – features available on Standard and Premium
