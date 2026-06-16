---
title: "Cosmos DB Partitioning"
type: concept
tags: [cosmos-db, partitioning, partition-key, scalability, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_3-cosmos-db-resource-hierarchy.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Cosmos DB Partitioning

## Overview

Partitioning is the mechanism [[azure-cosmos-db]] uses to elastically scale storage and throughput. The service transparently distributes data across partitions using a partition key chosen at container creation.

## Partition Types

### Physical Partition

The underlying storage and compute unit:
- Max throughput: **10,000 RU/s**
- Max storage: **50 GB**

### Logical Partition

An abstraction over physical partitions, grouping items that share the same partition key value:
- Max storage: **20 GB**

## Partition Key

- Must be specified when creating a [[cosmos-db-container|container]].
- Selected from a property on the items.
- Cosmos DB uses the key value to route data to the correct partition for writes, updates, deletes, and queries.
- Should be used in `WHERE` clauses for efficient data retrieval.

## Scaling Behavior

- **Scale out** (not up): increasing throughput or storage automatically adds physical partitions.
- Provides virtually unlimited throughput and storage per container.

## Related Pages

- [[azure-cosmos-db]] — parent service
- [[cosmos-db-container]] — the entity being partitioned
- [[request-units]] — throughput currency
- [[cosmos-db-resource-hierarchy]] — source page
