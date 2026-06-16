---
title: "Request Units (RUs)"
type: concept
tags: [cosmos-db, request-units, throughput, billing, performance, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_7-cosmos-db-request-units.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Request Units (RUs)

## Overview

A **Request Unit (RU)** is the normalized unit of cost for all database operations in [[azure-cosmos-db]]. It abstracts the underlying system resources (CPU, IOPS, memory) required to perform each operation.

## Key Facts

- **1 RU** = cost of a **point read** (fetch a single 1-KB item by its ID and partition key value).
- All operations — reads, writes, upserts, deletes, queries — are measured in RUs.
- Cost is **API-agnostic**: the same RU model applies regardless of which Cosmos DB API is used.
- You pay for **provisioned throughput** (RU/s) and **consumed storage** on an hourly basis.

## Operation Costs

| Operation | RU Cost |
|-----------|---------|
| Point read (1 KB item) | 1 RU |
| Insert | Higher than read (variable) |
| Upsert | Higher than read (variable) |
| Delete | Variable |
| Query | Variable (depends on complexity, data size) |

## Throughput Modes

### Provisioned Throughput Mode

- Provision a fixed number of **RU/s** (per second).
- Granularity: increments of **100 RU/s**.
- Can be scaled up or down at any time programmatically or via Azure portal.
- Configured at **container** or **database** level.

### Serverless Mode

- No throughput provisioning required.
- Billed for **actual RUs consumed** at the end of the billing period.
- Best for variable or unpredictable workloads.

## Related Pages

- [[azure-cosmos-db]] — the service
- [[cosmos-db-container]] — where throughput is provisioned
- [[cosmos-db-partitioning]] — how throughput relates to partitions (10,000 RU/s per physical partition)
- [[cosmos-db-request-units]] — source page
