---
title: "Azure Cosmos DB"
type: entity
tags: [cosmos-db, nosql, paas, azure, global-distribution, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_2-cosmos-db-benefits.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_3-cosmos-db-resource-hierarchy.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_6-cosmos-db-supported-apis.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_7-cosmos-db-request-units.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Cosmos DB

## What It Is

Azure Cosmos DB is a **fully managed NoSQL database** service on Microsoft Azure, designed for globally distributed applications requiring low latency, elastic scalability, and high availability.

## Core Design Goals

| Goal | Guarantee |
|------|-----------|
| Low latency | Reads and writes < 10 ms at P99 |
| High availability | 99.999% read and write availability (multi-region) |
| Elastic scalability | Unlimited throughput and storage via partitioning |
| Consistency flexibility | 5 well-defined consistency levels |

## Resource Hierarchy

```
Account
└── Database (namespace)
    └── Container (scalability unit, requires partition key)
        └── Items
```

See [[cosmos-db-container]] for container-level detail and [[cosmos-db-partitioning]] for partitioning mechanics.

## Supported APIs

| API | Data Model | Wire Protocol |
|-----|-----------|---------------|
| NoSQL (native) | JSON documents | Cosmos-native (SQL syntax) |
| MongoDB | BSON documents | MongoDB wire protocol |
| PostgreSQL | Relational / distributed tables | PostgreSQL + Citus |
| Apache Cassandra | Column-family | Cassandra wire protocol |
| Apache Gremlin | Graph (vertices + edges) | Gremlin |
| Table | Key/value | Azure Table Storage (OLTP only) |

See [[cosmos-db-apis]] for selection guidance.

## Throughput / Billing

All operations are measured in [[request-units|Request Units (RUs)]]. Two billing modes:
- **Provisioned throughput**: reserve RU/s in 100-RU increments.
- **Serverless**: pay for RUs actually consumed.

## Consistency

Five levels available: Strong, Bounded Staleness, Session, Consistent Prefix, Eventual. See [[cosmos-db-consistency-levels]].

## Global Distribution

Uses a **multi-master replication protocol** — every region supports reads and writes. Regions can be added or removed at any time without redeployment. See [[global-distribution]].

## Related Pages

- [[cosmos-db-container]] — scalability unit
- [[cosmos-db-partitioning]] — how data is distributed
- [[cosmos-db-consistency-levels]] — the five consistency levels
- [[cosmos-db-apis]] — API selection
- [[request-units]] — cost model
- [[global-distribution]] — multi-region replication
- [[cosmos-db-benefits]] — source: benefits overview
- [[cosmos-db-resource-hierarchy]] — source: resource hierarchy
- [[cosmos-db-supported-apis]] — source: API details
- [[cosmos-db-request-units]] — source: RU details
