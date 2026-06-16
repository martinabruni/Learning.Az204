---
title: "Azure Functions"
type: entity
tags: [azure-functions, serverless, paas, compute, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-functions_4-scale-azure-functions.pdf,
          learn.microsoft.com_en-us_training_modules_develop-azure-functions_2-azure-function-development-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Functions

## What It Is

Azure Functions is a **serverless compute service** on Azure that allows developers to run event-driven code without managing infrastructure. It is built on the **WebJobs SDK** and runs on Azure App Service infrastructure.

## Core Concepts

| Concept | Description |
|---------|-------------|
| Triggers | Define how a function is invoked; exactly one per function |
| Bindings | Declarative connections to input/output data sources; optional |
| Function app | Unit of deployment, management, and scaling |
| host.json | App-wide configuration file |
| local.settings.json | Local development settings (never commit to source control) |

## Supported Languages

C#, Java, JavaScript, TypeScript, Python, PowerShell.

> Starting with Functions 2.x, all functions in a function app must use the **same language**.

## Hosting Plans

| Plan | Scaling | Max Instances |
|------|---------|--------------|
| Consumption | Event driven, automatic | Win: 200 / Linux: 100 |
| Flex Consumption | Per-function, event driven | Memory-limited per region |
| Premium | Event driven, prewarmed | Win: 100 / Linux: 20–100 |
| Dedicated | Manual / autoscale | 10–30 (100 with ASE) |
| Container Apps | Event driven | 10–300 |

## Time-out Limits

- Consumption plan: default 5 min, max 10 min.
- All other plans: default 30 min, max unbounded.
- HTTP triggers: hard cap of **230 seconds** regardless of plan (Azure Load Balancer idle timeout).

## Comparison with Peers

| Service | Type | Orchestration model |
|---------|------|---------------------|
| Azure Functions | Serverless compute | Code-first (imperative) |
| Azure Logic Apps | Serverless workflow | Designer-first (declarative) |
| App Service WebJobs | Code-first integration | No serverless model, no browser dev |

## Related Pages

- [[function-app]] – unit of deployment
- [[triggers-and-bindings]] – core programming model
- [[functions-hosting-plans]] – hosting plan comparison
- [[durable-functions]] – orchestration extension
- [[managed-identity]] – identity-based connections
- [[serverless-computing]] – broader concept
- [[discover-azure-functions]] – source: overview
- [[compare-azure-functions-hosting-options]] – source: hosting plans
- [[scale-azure-functions]] – source: scaling
- [[explore-azure-functions-development]] – source: development
