---
title: "Wiki Index – AZ-204 Learning Path 2: Azure Functions"
type: synthesis
tags: [index, az204, azure-functions]
sources: [discover-azure-functions.md, compare-azure-functions-hosting-options.md, scale-azure-functions.md, explore-azure-functions-development.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 2: Azure Functions

This wiki is built from the 7 PDFs in `raw/`, covering two Microsoft Learn modules on Azure Functions.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-functions]] | Serverless compute service on Azure; event-driven, code-first, built on WebJobs SDK |
| [[function-app]] | Unit of deployment, management, and scaling for Azure Functions |
| [[azure-logic-apps]] | Serverless workflow integration platform; designer-first declarative orchestration |
| [[azure-container-apps]] | Fully managed container hosting environment; one of the Functions hosting options |

---

## Concepts

| Page | Summary |
|------|---------|
| [[serverless-computing]] | Cloud model with no server management, automatic scaling, and pay-per-use pricing |
| [[triggers-and-bindings]] | Core Functions programming model: triggers invoke functions; bindings connect data sources |
| [[functions-hosting-plans]] | Five hosting plans for Functions, each with different scaling, pricing, and timeout behaviors |
| [[cold-start]] | Latency on first invocation after idle; mitigated by Premium plan prewarmed workers or Flex pre-provisioned instances |
| [[durable-functions]] | Extension enabling stateful, long-running orchestrations in code |
| [[managed-identity]] | Azure AD identity for passwordless service-to-service authentication in Functions |

---

## Sources — Module 1: Explore Azure Functions

| Page | PDF |
|------|-----|
| [[discover-azure-functions]] | `explore-azure-functions_2-azure-functions-overview.pdf` |
| [[compare-azure-functions-hosting-options]] | `explore-azure-functions_3-compare-azure-functions-hosting-options.pdf` |
| [[scale-azure-functions]] | `explore-azure-functions_4-scale-azure-functions.pdf` |

## Sources — Module 2: Develop Azure Functions

| Page | PDF |
|------|-----|
| [[explore-azure-functions-development]] | `develop-azure-functions_2-azure-function-development-overview.pdf` |
| [[create-triggers-and-bindings]] | `develop-azure-functions_3-create-triggers-bindings.pdf` |
| [[connect-functions-to-azure-services]] | `develop-azure-functions_4-connect-azure-services.pdf` |
| [[exercise-create-function-visual-studio-code]] | `develop-azure-functions_5-create-function-visual-studio-code.pdf` |

---

## Cross-References to Learning Path 1

The following LP1 entities and concepts are referenced by LP2 pages:

- [[app-service-plan]] — used by Dedicated hosting plan
- [[app-service-environment]] — used by Dedicated plan at max scale (100 instances)
- [[application-settings]] — mechanism used by Functions to store connection secrets

---

## Page Counts

- Sources: 7
- Entities: 4
- Concepts: 6
- **Total wiki pages: 13** (plus this index and log.md)
