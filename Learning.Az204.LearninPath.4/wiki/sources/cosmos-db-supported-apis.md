---
title: "Explore Supported APIs"
type: source
tags: [cosmos-db, apis, nosql, mongodb, cassandra, gremlin, table, postgresql, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_6-cosmos-db-supported-apis.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Supported APIs

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_6-cosmos-db-supported-apis.pdf

Unit 6 of 10 — Module: Explore Azure Cosmos DB

## Overview

[[azure-cosmos-db]] offers multiple database APIs: **NoSQL, MongoDB, PostgreSQL, Cassandra, Gremlin, and Table**. All support automatic scaling of storage and throughput, flexibility, and performance guarantees.

> "There's no one best API, and you can choose any one of the APIs to build your application."

## Key Selection Guidance

- **API for NoSQL** is native to Azure Cosmos DB — best end-to-end experience; new features arrive here first.
- **MongoDB, PostgreSQL, Cassandra, Gremlin, Table** implement the wire protocol of open-source engines — choose these when migrating existing apps or leveraging existing skills/tooling.

## API Details

### API for NoSQL

- Stores data as **JSON documents** (items).
- Querying via **SQL syntax**.
- Native API; first to receive new Cosmos DB features.
- Full control over interface, service, and SDK client libraries.

### API for MongoDB

- Stores data in document structure via **BSON format**.
- Compatible with **MongoDB wire protocol** (no native MongoDB code).
- Best for teams with MongoDB ecosystem skills.

### API for PostgreSQL

- Managed service for PostgreSQL at any scale.
- Uses **Citus open-source** for distributed tables.
- Can run on a single node or in a multi-node configuration.

### API for Apache Cassandra

- Stores data in **column-oriented schema**.
- Wire-protocol compatible with native Apache Cassandra.
- Suited for large volumes of data with flexible column-oriented schemas.

### API for Apache Gremlin

- Stores data as **edges and vertices** (graph model).
- Use for: dynamic data, complex relations, data too complex for relational databases, or existing Gremlin skills.

### API for Table

- Stores data in **key/value format**.
- Recommended migration path from **Azure Table Storage** (overcomes limitations in latency, scaling, throughput, global distribution, indexing, query performance).
- Supports **OLTP scenarios only**.

## Related Pages

- [[azure-cosmos-db]] — entity page
- [[cosmos-db-apis]] — concept page
- [[choose-cosmos-db-consistency-level]] — previous unit
- [[cosmos-db-request-units]] — next unit
