---
title: "Explore Consistency Levels"
type: source
tags: [cosmos-db, consistency, distributed-systems, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_4-cosmos-db-consistency-levels-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Consistency Levels

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_4-cosmos-db-consistency-levels-overview.pdf

Unit 4 of 10 — Module: Explore Azure Cosmos DB

## Overview

[[azure-cosmos-db]] approaches data consistency as a **spectrum** rather than two binary extremes. Five well-defined levels are available, each providing availability and performance tradeoffs.

## The Five Consistency Levels (Strongest to Weakest)

1. **Strong**
2. **Bounded staleness**
3. **Session**
4. **Consistent prefix**
5. **Eventual**

Moving from Strong toward Eventual: higher availability, lower latency, higher throughput.

## Key Claims

- Consistency levels are **region-agnostic**: guaranteed regardless of the region serving reads/writes, the number of regions, or whether the account has single or multiple write regions.
- Read consistency applies to **a single read operation scoped within a partition-key range or a logical partition**.

## Related Pages

- [[azure-cosmos-db]] — entity page
- [[cosmos-db-consistency-levels]] — concept page (full detail)
- [[choose-cosmos-db-consistency-level]] — next unit with per-level details
- [[cosmos-db-resource-hierarchy]] — previous unit
