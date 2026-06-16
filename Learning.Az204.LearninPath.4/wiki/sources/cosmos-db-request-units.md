---
title: "Discover Request Units"
type: source
tags: [cosmos-db, request-units, throughput, billing, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_7-cosmos-db-request-units.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Request Units

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_7-cosmos-db-request-units.pdf

Unit 7 of 10 — Module: Explore Azure Cosmos DB

## Overview

With [[azure-cosmos-db]], you pay for **provisioned throughput** and **consumed storage** on an hourly basis. All database operation costs are normalized and expressed as **Request Units (RUs)**.

A Request Unit represents the combined system resources (CPU, IOPS, memory) needed to perform database operations.

## Key Claims

- A **point read** (fetching a single 1-KB item by its ID and partition key) costs **1 RU**.
- All operations — reads, writes, upserts, deletes, queries — are measured in RUs.
- RU cost applies regardless of which API is used.
- Throughput must be provisioned to ensure sufficient resources are always available.

## Throughput/Billing Modes

| Mode | Description |
|------|-------------|
| **Provisioned throughput** | Provision RU/s at account creation, in increments of 100 RU/s. Can be scaled up or down at any time programmatically or via portal. Can be set at container or database level. |
| **Serverless** | No throughput provisioning. Billed for RUs actually consumed at end of billing period. |

## Relevant Quote

> "The cost of all database operations is normalized in Azure Cosmos DB and expressed by request units (or RUs, for short). A request unit represents the system resources such as CPU, IOPS, and memory that are required to perform the database operations supported by Azure Cosmos DB."

## Related Pages

- [[azure-cosmos-db]] — entity page
- [[request-units]] — concept page
- [[cosmos-db-supported-apis]] — previous unit
