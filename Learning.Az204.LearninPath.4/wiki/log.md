---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204]
sources: [index.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2026-06-16] ingest | AZ-204 Learning Path 4 — Azure Cosmos DB (6 PDFs)

**Raw sources processed:** 6 PDFs from Microsoft Learn module `explore-azure-cosmos-db` (units 2–7).

**Files Added:**

*Sources (6):*
- `sources/cosmos-db-benefits.md`
- `sources/cosmos-db-resource-hierarchy.md`
- `sources/cosmos-db-consistency-levels-overview.md`
- `sources/choose-cosmos-db-consistency-level.md`
- `sources/cosmos-db-supported-apis.md`
- `sources/cosmos-db-request-units.md`

*Entities (2):*
- `entities/azure-cosmos-db.md`
- `entities/cosmos-db-container.md`

*Concepts (5):*
- `concepts/global-distribution.md`
- `concepts/cosmos-db-partitioning.md`
- `concepts/cosmos-db-consistency-levels.md`
- `concepts/cosmos-db-apis.md`
- `concepts/request-units.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Azure Cosmos DB** is a fully managed NoSQL PaaS database with global distribution, multi-master replication, 99.999% availability SLA (multi-region), and sub-10 ms P99 latency.
- **Resource hierarchy**: Account → Database (namespace) → Container (scalability unit, requires partition key) → Items. Max 50 accounts per subscription.
- **Partitioning**: Physical partitions handle up to 10,000 RU/s and 50 GB; logical partitions up to 20 GB. Container throughput can be dedicated (standard or autoscale) or shared (database-level, up to 25 containers).
- **Consistency spectrum** (5 levels, strongest to weakest): Strong, Bounded Staleness, Session, Consistent Prefix, Eventual. Default set at account level; 100% of reads guaranteed to meet chosen level. Levels are region-agnostic.
- **Session consistency** is the most commonly recommended default: guarantees read-your-writes and write-follows-reads within a client session.
- **Bounded Staleness** is the go-to for multi-region write scenarios requiring bounded lag (configurable by K versions or T time interval).
- **Eventual consistency** is best for social counters (likes, retweets) where ordering is not required.
- **Six APIs**: NoSQL (native, features first), MongoDB (BSON, wire-protocol compatible), PostgreSQL (Citus distributed tables), Apache Cassandra (column-family), Apache Gremlin (graph), Table (key/value, OLTP only — recommended migration from Azure Table Storage).
- **Request Units (RUs)**: universal cost abstraction for all operations (CPU + IOPS + memory). Point read of a 1-KB item = 1 RU. Two billing modes: Provisioned (100 RU/s increments, per container or database) and Serverless (pay per RU consumed).

**Contradictions found:** None detected across the 6 source documents.
