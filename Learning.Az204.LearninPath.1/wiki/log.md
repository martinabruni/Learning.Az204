---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204]
sources: [index.md]
created: 2025-01-15
updated: 2026-05-15
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2025-01-15] ingest | AZ-204 Learning Path 1 — Azure App Service (23 PDFs)

**Raw sources processed:** 23 PDFs across 4 Microsoft Learn modules.

**Modules ingested:**
1. `configure-web-app-settings` (6 units)
2. `introduction-to-azure-app-service` (7 units)
3. `scale-apps-app-service` (5 units)
4. `understand-app-service-deployment-slots` (5 units)

**Files Added:**

*Sources (23):*
- `sources/configure-web-app-settings-introduction.md`
- `sources/configure-application-settings.md`
- `sources/configure-general-settings.md`
- `sources/configure-path-mappings.md`
- `sources/enable-diagnostic-logging.md`
- `sources/configure-security-certificates.md`
- `sources/intro-app-service-introduction.md`
- `sources/examine-azure-app-service.md`
- `sources/examine-app-service-plans.md`
- `sources/deploy-code-to-app-service.md`
- `sources/authentication-authorization-app-service.md`
- `sources/network-features-app-service.md`
- `sources/exercise-deploy-containerized-app.md`
- `sources/scale-apps-introduction.md`
- `sources/autoscale-factors.md`
- `sources/autoscale-conditions-rules-source.md`
- `sources/enable-autoscale-app-service.md`
- `sources/autoscale-best-practices-source.md`
- `sources/deployment-slots-introduction.md`
- `sources/staging-environments.md`
- `sources/slot-swapping-mechanics.md`
- `sources/swap-deployment-slots.md`
- `sources/route-traffic-app-service.md`

*Entities (5):*
- `entities/azure-app-service.md`
- `entities/app-service-plan.md`
- `entities/deployment-slot.md`
- `entities/autoscale.md`
- `entities/app-service-environment.md`

*Concepts (12):*
- `concepts/application-settings.md`
- `concepts/general-settings.md`
- `concepts/path-mappings.md`
- `concepts/diagnostic-logging.md`
- `concepts/security-certificates.md`
- `concepts/authentication-authorization.md`
- `concepts/networking-features.md`
- `concepts/container-deployment.md`
- `concepts/autoscale-conditions-rules.md`
- `concepts/autoscale-best-practices.md`
- `concepts/slot-swapping.md`
- `concepts/traffic-routing.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Azure App Service** is a fully managed PaaS supporting .NET, Java, Node.js, Python, PHP, and custom containers on Windows and Linux.
- **App Service Plan** determines compute tier, OS, region, and determines feature availability: Free/Shared have no scale-out; Standard+ enables slots and autoscale; Isolated runs in a dedicated VNet.
- **Application settings** are always encrypted at rest and override `Web.config`/`appsettings.json`; changes trigger app restart; settings can be slot-sticky.
- **Always On** is required for continuous WebJobs and CRON-triggered WebJobs; without it, apps unload after 20 minutes.
- **Diagnostic logging** has five types; Application logging auto-disables after 12 hours on file system; Deployment logging is always on.
- **EasyAuth** provides federated identity with Microsoft Entra ID, Google, Facebook, GitHub, X, Apple, and OpenID Connect — without application code changes.
- **Deployment slots** require Standard tier or higher; provide zero-downtime swaps, instant rollback, and A/B traffic routing via `x-ms-routing-name` cookie.
- **Slot swapping** is a multi-step process: apply target settings → wait for restart → warm-up → switch routing rules.
- **Auto swap** (Windows only) triggers automatically on code push.
- **Autoscale** (rules-based, Standard+) scales out/in based on metrics or schedules; Automatic Scaling (platform-managed, Premium V2/V3+) handles it without user-defined rules.
- **Autoscale best practice**: use different thresholds for scale-out and scale-in to prevent flapping; always pair scale-out with scale-in rules.
- **App Service Environment (ASE)** is a single-tenant Isolated deployment inside a customer VNet, providing maximum scale-out and network isolation.

**Contradictions found:** None detected across the 23 source documents. Settings are consistent across units — e.g. the requirement for Standard tier for deployment slots is stated consistently in both the introduction-to-azure-app-service and understand-app-service-deployment-slots modules.

---

## [2026-05-15] lint | AZ-204 Learning Path 1 wiki semantic lint

**Scope:** contradictions, stale content, orphan pages, missing wiki links, semantic gaps, missing cross-references.

**Health-check metrics:**
- Pages analyzed: 42
- Wikilinks analyzed: 302
- Missing wikilinks: 0
- Orphan pages: 0

**Files Updated:**
- `entities/azure-app-service.md` (autoscale wording corrected: horizontal autoscale vs manual scale up/down)
- `concepts/slot-swapping.md` (completed swapped vs slot-specific settings list: WebJobs content/schedulers, diagnostic settings, CORS, publishing endpoints)

**Open suggestions (not auto-applied):**
- Add a dedicated concept page for deployment methods / CI-CD.
- Add a dedicated page for WebJobs.
- Add an entity stub for Azure Key Vault in App Service context.
