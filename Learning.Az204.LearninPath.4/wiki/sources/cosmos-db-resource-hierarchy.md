---
title: "Explore the Resource Hierarchy"
type: source
tags: [cosmos-db, resource-hierarchy, containers, partitions, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_3-cosmos-db-resource-hierarchy.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore the Resource Hierarchy

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-cosmos-db_3-cosmos-db-resource-hierarchy.pdf

Unit 3 of 10 — Module: Explore Azure Cosmos DB

## Overview

The [[azure-cosmos-db]] resource hierarchy is: **Account → Database → Container → Item**.

The **Cosmos DB account** is the fundamental unit of global distribution and high availability. It has a unique DNS name and can be managed via the Azure portal, Azure CLI, or language-specific SDKs.

## Key Claims

- Max **50 Cosmos DB accounts** per Azure subscription (can be increased via support request).
- A **database** is analogous to a namespace and is the unit of management for a set of containers.
- A **container** is the fundamental unit of scalability; it has virtually unlimited provisioned throughput (RU/s) and storage.
- Cosmos DB transparently partitions a container using the **logical partition key** specified at creation.
- A **physical partition** can handle up to **10,000 RU/s** and store up to **50 GB** of data.
- A **logical partition** can store up to **20 GB** of data.

## Container Throughput Modes

| Mode | Description |
|------|-------------|
| Dedicated throughput | Reserved exclusively for that container; standard or autoscale sub-types |
| Shared throughput | Specified at database level; shared with up to 25 containers in the database |

## Items per API

| Azure Cosmos DB entity | API for NoSQL | API for Cassandra | API for MongoDB | API for Gremlin | API for Table |
|------------------------|---------------|-------------------|-----------------|-----------------|---------------|
| Azure Cosmos DB item   | Item          | Row               | Document        | Node or edge    | Item          |

## Related Pages

- [[azure-cosmos-db]] — entity page
- [[cosmos-db-container]] — entity page
- [[cosmos-db-partitioning]] — concept
- [[request-units]] — concept
- [[cosmos-db-benefits]] — previous unit
- [[cosmos-db-consistency-levels-overview]] — next unit
