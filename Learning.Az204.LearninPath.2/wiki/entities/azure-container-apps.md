---
title: "Azure Container Apps"
type: entity
tags: [azure-container-apps, containers, serverless, kubernetes, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-functions_4-scale-azure-functions.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Container Apps

## What It Is

Azure Container Apps is a fully managed environment for deploying containerized applications. It is one of the hosting options for [[azure-functions]], supporting Linux containers.

## As a Functions Hosting Option

- Deploys containerized function apps in a fully managed environment.
- Uses the Azure Functions programming model for event-driven, cloud native functions.
- Runs functions alongside microservices, APIs, websites, and workflows as container-hosted programs.
- Supports Linux containers only.
- Event-driven scaling: adds Functions host instances based on trigger events.
- Max instances: **10–300** (configurable max replicas, subject to cores quota).

## When to Use for Functions

- Packaging custom libraries with function code (line-of-business apps).
- Migrating on-premises or legacy apps to cloud native microservices in containers.
- Avoiding overhead of managing Kubernetes clusters.
- Needing high-end processing power with dedicated CPU compute resources.

## Related Pages

- [[azure-functions]] – hosted service
- [[functions-hosting-plans]] – plan comparison
- [[scale-azure-functions]] – scaling details
- [[compare-azure-functions-hosting-options]] – source
