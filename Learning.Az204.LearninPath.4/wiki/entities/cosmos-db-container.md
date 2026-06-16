---
title: "Azure Cosmos DB Container"
type: entity
tags: [cosmos-db, container, partitioning, throughput, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_3-cosmos-db-resource-hierarchy.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Cosmos DB Container

## What It Is

An Azure Cosmos DB container is the **fundamental unit of scalability** in [[azure-cosmos-db]]. It provides virtually unlimited provisioned throughput (RU/s) and storage, achieved via transparent partitioning.

## Key Properties

- Requires a **partition key** at creation time — used by Cosmos DB to route data to partitions efficiently.
- Scales **out** (more partitions), unlike relational databases that scale up.
- Partitioning is transparent to the application.

## Partitioning Limits

| Partition type | Max throughput | Max storage |
|----------------|---------------|-------------|
| Physical partition | 10,000 RU/s | 50 GB |
| Logical partition | — | 20 GB |

See [[cosmos-db-partitioning]] for detail.

## Throughput Modes

| Mode | Description |
|------|-------------|
| Dedicated (standard) | Throughput reserved exclusively for this container |
| Dedicated (autoscale) | Throughput auto-scales within configured bounds |
| Shared | Throughput set at database level; shared across up to 25 containers |

## API Representation

Depending on the API used, a container is surfaced as:
- NoSQL: container
- MongoDB: collection
- Cassandra: table
- Gremlin: graph
- Table: table

## Related Pages

- [[azure-cosmos-db]] — parent service
- [[cosmos-db-partitioning]] — partitioning mechanics
- [[request-units]] — throughput measurement unit
- [[cosmos-db-resource-hierarchy]] — source page
