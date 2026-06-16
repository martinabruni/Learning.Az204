---
title: "Queue Solution Decision Framework"
type: concept
tags: [messaging, decision-guide, service-bus, queue-storage, az204]
sources: [choose-queue-solution.md]
created: 2026-06-16
updated: 2026-06-16
---

# Queue Solution Decision Framework

## Overview

Azure offers two queuing technologies: [[azure-service-bus]] and [[azure-queue-storage]]. They can be used independently or together depending on solution requirements.

## Decision Matrix

| Requirement | Service Bus | Queue Storage |
|-------------|:-----------:|:-------------:|
| Guaranteed FIFO delivery | Yes | No |
| Automatic duplicate detection | Yes | No |
| Transactional send/receive | Yes | No |
| Messages > 64 KB (up to 100 MB) | Yes | No |
| Topics / pub-sub (1:n) | Yes | No |
| Long-polling (no polling needed) | Yes | No |
| Parallel long-running streams (sessions) | Yes | No |
| Role-based access model | Yes | No |
| Store > 80 GB of messages | No | Yes |
| Per-message progress tracking | No | Yes |
| Server-side transaction logs | No | Yes |

## Key Differentiators

### Service Bus advantages
- Enterprise-grade: FIFO, transactions, deduplication, sessions.
- Supports publish-subscribe (topics + subscriptions).
- Supports messages up to 100 MB on Premium tier.
- TCP-based long-polling eliminates the need for active polling.

### Queue Storage advantages
- Handles massive queue sizes (80+ GB).
- Server-side logging of all transactions for auditing.
- Simple message progress tracking for resilient worker patterns.
- Backed by Azure Storage — integrated with storage account capacity.

## Related Pages

- [[azure-service-bus]] – Service Bus entity
- [[azure-queue-storage]] – Queue Storage entity
- [[choose-queue-solution]] – source document
- [[publish-subscribe-pattern]] – pub/sub concept
- [[service-bus-advanced-features]] – advanced Service Bus features
