---
title: "Choose the Right Consistency Level"
type: source
tags: [cosmos-db, consistency, sla, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_5-choose-cosmos-db-consistency-level.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Choose the Right Consistency Level

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_5-choose-cosmos-db-consistency-level.pdf

Unit 5 of 10 — Module: Explore Azure Cosmos DB

## Overview

Each [[cosmos-db-consistency-levels|consistency model]] is backed by comprehensive SLAs and suited to specific real-world scenarios. The default consistency level is configured at the **account level** and applies to all databases and containers under that account. It can be changed at any time.

Cosmos DB **guarantees 100% of read requests** meet the consistency guarantee for the chosen level. Formal definitions use the TLA+ specification language (available in the azure-cosmos-tla GitHub repo).

## Consistency Levels Explained

### Strong Consistency

- Offers **linearizability**: reads always return the most recent committed version.
- A client never sees an uncommitted or partial write.
- Use when correctness is critical and latency is secondary.

### Bounded Staleness Consistency

- Data lag between any two regions is always less than a specified amount, configurable as:
  - **K versions** (number of updates) of an item, OR
  - **T time interval** reads might lag behind writes (whichever is reached first).
- Primarily beneficial for **single-region write accounts with two or more regions**.
- If data lag exceeds the staleness threshold, writes are **throttled** until within bounds.
- For single-region accounts: provides the same guarantees as Session and Eventual.
- Data is replicated to a local majority (3 replicas in a 4-replica set) in the single region.

### Session Consistency

- Within a single client session, guarantees:
  - **Read-your-writes**
  - **Write-follows-reads**
- Assumes a single "writer" session or shared session token for multiple writers.
- Writes replicated to minimum 3 replicas (in a 4-replica set) locally; asynchronous replication to other regions.

### Consistent Prefix Consistency

- Single document writes: eventual consistency.
- Batch writes within a transaction: returned consistent to that transaction.
- **Guarantee**: writes within a multi-document transaction are always visible together — no out-of-order reads across transaction boundaries.

### Eventual Consistency

- **No ordering guarantee** for reads.
- Replicas eventually converge in the absence of further writes.
- Weakest form — a client might read values older than ones previously read.
- Ideal for scenarios that don't require ordering: count of likes, retweets, non-threaded comments.

## Related Pages

- [[cosmos-db-consistency-levels]] — concept page
- [[azure-cosmos-db]] — entity page
- [[cosmos-db-consistency-levels-overview]] — previous unit
- [[cosmos-db-supported-apis]] — next unit
