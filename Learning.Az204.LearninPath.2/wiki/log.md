---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204]
sources: [index.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2026-06-16] ingest | AZ-204 Learning Path 2 — Azure Functions (7 PDFs)

**Raw sources processed:** 7 PDFs across 2 Microsoft Learn modules.

**Modules ingested:**
1. `explore-azure-functions` (units 2–4)
2. `develop-azure-functions` (units 2–5)

**Files Added:**

*Sources (7):*
- `sources/discover-azure-functions.md`
- `sources/compare-azure-functions-hosting-options.md`
- `sources/scale-azure-functions.md`
- `sources/explore-azure-functions-development.md`
- `sources/create-triggers-and-bindings.md`
- `sources/connect-functions-to-azure-services.md`
- `sources/exercise-create-function-visual-studio-code.md`

*Entities (4):*
- `entities/azure-functions.md`
- `entities/function-app.md`
- `entities/azure-logic-apps.md`
- `entities/azure-container-apps.md`

*Concepts (6):*
- `concepts/serverless-computing.md`
- `concepts/triggers-and-bindings.md`
- `concepts/functions-hosting-plans.md`
- `concepts/cold-start.md`
- `concepts/durable-functions.md`
- `concepts/managed-identity.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Azure Functions** is a serverless compute service built on the WebJobs SDK; it is the preferred choice over WebJobs for most scenarios due to better developer productivity, more language options, pay-per-use pricing, browser-based dev/test, and Logic Apps integration.
- **Five hosting plans**: Consumption (default, pay-per-use, max 10 min), Flex Consumption (per-function scaling, VNet, always-ready instances), Premium (prewarmed, no cold start, VNet), Dedicated (App Service plan rates, manual/autoscale, requires Always On), Container Apps (containerized, 10–300 instances).
- **HTTP trigger hard cap**: 230 seconds regardless of plan (Azure Load Balancer idle timeout). Use Durable Functions async pattern for longer HTTP workflows.
- **Triggers and bindings**: every function has exactly one trigger; bindings are optional declarative connections to data sources. Language determines how they are configured (attributes, annotations, `function.json`, or decorators). Cannot mix programming models within a function app.
- **function.json**: legacy approach for Node.js v3, Python v1, PowerShell. Modern models (Node.js v4, Python v2) generate it from code — do not edit directly in portal.
- **Function app project files**: `host.json` (app-wide config, never modify directly in portal for modern models) and `local.settings.json` (local dev only, **never commit to source control**).
- **Identity-based connections**: preferred over connection strings; use system-assigned managed identity by default; apply principle of least privilege. Azure Files does not support managed identity — must use connection string settings.
- **Durable Functions** is the preferred mechanism for long-running orchestrations; the Dedicated plan is noted as an alternative "where Durable Functions can't be used."
- **Cross-LP references**: Dedicated plan uses App Service Plan and App Service Environment entities from LP1; Functions reuses the Application Settings concept from LP1.

**Contradictions found:** None detected. LP2 content is consistent with LP1 — the reference to App Service plan, App Service Environment, and application settings aligns with LP1's established definitions. The description of Functions using the WebJobs SDK is consistent with LP1's WebJobs coverage in the App Service context.
