---
title: "Global Distribution"
type: concept
tags: [cosmos-db, global-distribution, multi-master, replication, high-availability, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_2-cosmos-db-benefits.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Global Distribution

## Overview

Global distribution in [[azure-cosmos-db]] allows data to be replicated automatically across any number of Azure regions, with every region capable of both reads and writes via a **multi-master replication protocol**.

## Key Characteristics

- **Multi-master**: every configured region accepts reads and writes — no single primary.
- **Elastic scalability**: unlimited read and write scalability across regions.
- **Automatic failover**: if a region becomes unavailable, other regions automatically handle requests.
- **Dynamic region management**: regions can be added or removed at any time without pausing or redeploying the application.
- **Consistency with guarantees**: data replication between regions is governed by the selected [[cosmos-db-consistency-levels|consistency level]].

## SLA Guarantees

| Metric | Value |
|--------|-------|
| Read and write availability (multi-region) | 99.999% |
| Read and write latency | < 10 ms at the 99th percentile |

## Best Practice

Place data in the regions closest to your users to minimize latency. The required regions depend on the global reach of the application and user locations.

## Related Pages

- [[azure-cosmos-db]] — the service
- [[cosmos-db-consistency-levels]] — how consistency works across regions
- [[cosmos-db-benefits]] — source page
