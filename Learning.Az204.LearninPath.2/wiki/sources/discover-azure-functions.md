---
title: "Discover Azure Functions"
type: source
tags: [azure-functions, serverless, logic-apps, webjobs, triggers, bindings, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Azure Functions

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf

## Overview

[[azure-functions]] is a serverless solution that allows writing less code, maintaining less infrastructure, and saving on costs. The cloud infrastructure provides all resources needed to keep applications running.

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf
> "Azure Functions is a serverless solution that allows you to write less code, maintain less infrastructure, and save on costs."

Azure Functions supports **triggers** (ways to start execution) and **bindings** (ways to simplify coding for input and output data).

## Compare Azure Functions and Azure Logic Apps

Both are Azure Services enabling serverless workloads:

- **Azure Functions**: serverless **compute** service — code-first (imperative)
- **Azure Logic Apps**: serverless **workflow integration** platform — designer-first (declarative)

Both can create complex **orchestrations**. For Functions, orchestrations are built with code and the [[durable-functions]] extension; for Logic Apps, via GUI or configuration files.

| Topic | Azure Functions | Logic Apps |
|-------|----------------|------------|
| Development | Code-first (imperative) | Designer-first (declarative) |
| Connectivity | ~dozen built-in binding types; write code for custom | Large connector collection; Enterprise Integration Pack for B2B |
| Actions | Each activity is an Azure function | Large collection of ready-made actions |
| Monitoring | Azure Application Insights | Azure portal, Azure Monitor logs |
| Management | REST API, Visual Studio | Azure portal, REST API, PowerShell, Visual Studio |
| Execution context | Azure or locally | Azure, locally, or on premises |

## Compare Azure Functions and WebJobs

[[azure-app-service]] WebJobs with the WebJobs SDK is also code-first. **Azure Functions is built on the WebJobs SDK**, sharing event triggers and Azure service connections.

| Factor | Azure Functions | WebJobs with WebJobs SDK |
|--------|----------------|--------------------------|
| Serverless app model with automatic scaling | Yes | No |
| Develop and test in browser | Yes | No |
| Pay-per-use pricing | Yes | No |
| Integration with Logic Apps | Yes | No |
| Trigger events | Timer, Storage queues/blobs, Service Bus, Cosmos DB, Event Hubs, HTTP/WebHook, Event Grid | Timer, Storage queues/blobs, Service Bus, Cosmos DB, Event Hubs, File system |

> [!source] learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf
> "Azure Functions offers more developer productivity than Azure App Service WebJobs does. It also offers more options for programming languages, development environments, Azure service integration, and pricing. For most scenarios, it's the best choice."

## Key Claims

- Functions is the preferred choice over WebJobs for most scenarios.
- Functions adds HTTP/WebHook and Azure Event Grid triggers not available in WebJobs.
- Both Functions and Logic Apps can orchestrate complex multi-step workflows.

## Related Pages

- [[azure-functions]] – entity page
- [[serverless-computing]] – concept
- [[triggers-and-bindings]] – concept
- [[durable-functions]] – concept
- [[compare-azure-functions-hosting-options]] – next source
