---
title: "Azure Logic Apps"
type: entity
tags: [azure-logic-apps, serverless, workflow, integration, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Logic Apps

## What It Is

Azure Logic Apps is a **serverless workflow integration platform** on Azure. It enables building complex orchestrations (sequences of steps called _actions_) through a designer-first (declarative) approach.

## Comparison with Azure Functions

| Topic | Azure Logic Apps | Azure Functions |
|-------|-----------------|----------------|
| Development | Designer-first (declarative) | Code-first (imperative) |
| Connectivity | Large connector collection; Enterprise Integration Pack for B2B | ~dozen built-in binding types; custom bindings via code |
| Actions | Large collection of ready-made actions | Each activity is a coded Azure function |
| Monitoring | Azure portal, Azure Monitor logs | Azure Application Insights |
| Management | Azure portal, REST API, PowerShell, Visual Studio | REST API, Visual Studio |
| Execution context | Azure, locally, or on premises | Azure or locally |

## Orchestrations

An orchestration is a collection of functions or steps (called **actions** in Logic Apps) executed to accomplish a complex task. Logic Apps creates orchestrations via GUI or configuration files.

## Related Pages

- [[azure-functions]] – peer service (serverless compute)
- [[serverless-computing]] – broader concept
- [[discover-azure-functions]] – source with comparison table
