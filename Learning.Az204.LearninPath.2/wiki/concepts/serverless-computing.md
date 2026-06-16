---
title: "Serverless Computing"
type: concept
tags: [serverless, azure-functions, logic-apps, cloud, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Serverless Computing

## Definition

Serverless computing is a cloud execution model where the cloud provider automatically manages infrastructure provisioning, scaling, and maintenance. Developers write code and deploy it without worrying about servers.

## Key Characteristics

- No server management by the developer.
- Automatic scaling based on demand.
- Pay-per-use pricing (pay only for actual execution/consumption).
- Event-driven execution model.

## Azure Serverless Services

| Service | Type |
|---------|------|
| [[azure-functions]] | Serverless compute |
| [[azure-logic-apps]] | Serverless workflow integration |

## Orchestrations

A complex serverless pattern is **orchestration** — a collection of functions or steps executed to accomplish a complex task. Both Azure Functions (via [[durable-functions]]) and Logic Apps support orchestrations.

## Related Pages

- [[azure-functions]] – Azure's primary serverless compute service
- [[azure-logic-apps]] – serverless workflow platform
- [[durable-functions]] – stateful orchestration extension for Functions
- [[functions-hosting-plans]] – how serverless scaling works for Functions
- [[discover-azure-functions]] – source
