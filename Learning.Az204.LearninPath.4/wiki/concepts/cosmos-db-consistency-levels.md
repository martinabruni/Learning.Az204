---
title: "Cosmos DB Consistency Levels"
type: concept
tags: [cosmos-db, consistency, distributed-systems, sla, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_4-cosmos-db-consistency-levels-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_5-choose-cosmos-db-consistency-level.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Cosmos DB Consistency Levels

## Overview

[[azure-cosmos-db]] treats data consistency as a **spectrum** rather than a binary choice. Five well-defined levels are available, from strongest to weakest:

```
Strong → Bounded Staleness → Session → Consistent Prefix → Eventual
  ↑                                                              ↑
Stronger Consistency                             Higher availability,
                                                 lower latency,
                                                 higher throughput
```

Consistency levels are **region-agnostic** — guaranteed regardless of: the region serving reads/writes, number of regions, or single vs. multiple write regions.

Cosmos DB guarantees **100% of read requests** meet the selected consistency guarantee.

## Default Configuration

Set at the **account level** — applies to all databases and containers. Can be changed at any time.

## Level Details

### 1. Strong

- **Guarantee**: linearizability — reads always return the most recent committed version.
- A client never sees uncommitted or partial writes.
- Highest correctness; highest latency cost.

### 2. Bounded Staleness

- **Guarantee**: lag between any two regions is within a configurable bound of either:
  - **K versions** (number of item updates), OR
  - **T time interval** (whichever is reached first)
- When lag exceeds the bound, writes for that partition are **throttled** until within bounds again.
- Primarily beneficial for **single-region write accounts with 2+ regions**.
- For single-region accounts: equivalent to Session and Eventual.
- Replication: 3 replicas in a 4-replica set (local majority).

### 3. Session

- **Guarantee** (within a single client session):
  - **Read-your-writes**: a client always reads what it just wrote.
  - **Write-follows-reads**: writes are ordered after the last read.
- Requires a single "writer" session or shared session token across writers.
- Replication: minimum 3 replicas locally; asynchronous to other regions.

### 4. Consistent Prefix

- **Guarantee**: reads never see out-of-order writes.
  - Single document writes: eventual consistency.
  - Multi-document transactional writes: always visible together (no partial transaction reads).
- Example: if writes happen as T1 (Doc1 v1, Doc2 v1) then T2 (Doc1 v2, Doc2 v2), a read returns either the T1 or T2 state — never a mixed state.

### 5. Eventual

- **Guarantee**: no ordering guarantee for reads; replicas eventually converge.
- Weakest level — a client may read values older than previously read values.
- Highest availability, lowest latency, highest throughput.
- Ideal for: social counters (likes, retweets), non-threaded comments.

## Choosing the Right Level

| Scenario | Recommended Level |
|----------|-----------------|
| Financial transactions, inventory | Strong |
| Multi-region apps needing bounded lag | Bounded Staleness |
| Most apps (user sessions, shopping carts) | Session (default recommendation) |
| Collaborative apps needing ordered writes | Consistent Prefix |
| Social media counters, analytics | Eventual |

## Related Pages

- [[azure-cosmos-db]] — the service
- [[global-distribution]] — how replication interacts with consistency
- [[cosmos-db-consistency-levels-overview]] — source: overview unit
- [[choose-cosmos-db-consistency-level]] — source: per-level detail unit
