---
title: "Cosmos DB APIs"
type: concept
tags: [cosmos-db, apis, nosql, mongodb, cassandra, gremlin, table, postgresql, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_6-cosmos-db-supported-apis.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Cosmos DB APIs

## Overview

[[azure-cosmos-db]] supports six database APIs. All offer automatic scaling of storage and throughput, flexibility, and performance guarantees. There is no single best API — the choice depends on your existing stack and use case.

## API Summary

| API | Data Model | Wire Protocol | Best For |
|-----|-----------|---------------|----------|
| **NoSQL** (native) | JSON documents | Cosmos-native + SQL | New Cosmos DB projects; best features first |
| **MongoDB** | BSON documents | MongoDB | Existing MongoDB apps/skills |
| **PostgreSQL** | Relational / distributed | PostgreSQL + Citus | PostgreSQL workloads at scale |
| **Apache Cassandra** | Column-family | Cassandra | Large volumes, flexible column schema |
| **Apache Gremlin** | Graph (vertices + edges) | Gremlin | Complex relationships, graph traversal |
| **Table** | Key/value | Azure Table Storage | Migration from Azure Table Storage (OLTP) |

## Selection Guide

### Choose NoSQL when:
- Starting a new project on Cosmos DB.
- You want the latest Cosmos DB features (they land here first).
- You need SQL-syntax querying over JSON.

### Choose a compatibility API (MongoDB, Cassandra, Gremlin, Table, PostgreSQL) when:
- You have existing applications in that ecosystem.
- You don't want to rewrite your data access layer.
- You want to leverage existing open-source tooling and expertise.

## Notable Details

- **API for NoSQL**: new Cosmos DB features ship here first.
- **API for MongoDB**: BSON format, MongoDB wire-protocol compatible, but no native MongoDB code under the hood.
- **API for PostgreSQL**: powered by Citus for distributed tables; single-node or multi-node.
- **API for Cassandra**: wire-protocol compatible with native Apache Cassandra.
- **API for Gremlin**: graph storage as edges and vertices; ideal for complex relational data.
- **API for Table**: overcomes Azure Table Storage limitations; supports **OLTP scenarios only**.

## Related Pages

- [[azure-cosmos-db]] — parent service
- [[cosmos-db-supported-apis]] — source page
- [[cosmos-db-container]] — containers serve items differently per API
