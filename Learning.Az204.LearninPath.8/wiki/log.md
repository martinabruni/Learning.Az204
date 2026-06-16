---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204, api-management]
sources: [index.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2026-06-16] ingest | AZ-204 Learning Path 8 — Azure API Management (6 PDFs)

**Raw sources processed:** 6 PDFs from 1 Microsoft Learn module (`explore-api-management`, units 2–7).

**Files Added:**

*Sources (6):*
- `sources/api-management-overview.md`
- `sources/api-gateways.md`
- `sources/api-management-policies.md`
- `sources/create-advanced-policies.md`
- `sources/secure-access-api-subscriptions.md`
- `sources/secure-access-api-certificates.md`

*Entities (2):*
- `entities/azure-api-management.md`
- `entities/azure-event-hubs.md`

*Concepts (7):*
- `concepts/apim-gateway.md`
- `concepts/apim-policies.md`
- `concepts/apim-advanced-policies.md`
- `concepts/apim-products.md`
- `concepts/apim-subscriptions.md`
- `concepts/apim-certificates.md`
- `concepts/tls-mutual-auth.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key takeaways:**
- **Azure API Management** has three core components: API gateway (data plane), management plane (admin interface), and developer portal (self-service documentation and keys).
- **API gateway** acts as a reverse proxy; without it, clients must call backends directly, causing coupling, complex client code, and fragmented cross-cutting concerns. Supports **managed** (Azure-hosted) and **self-hosted** (containerized, for hybrid/multicloud) deployment modes.
- **Policies** are XML documents with four sections (`inbound`, `backend`, `outbound`, `on-error`); applied sequentially by the gateway; support C# expressions via `@(expr)` and `@{block}` syntax; scoped globally, per-product, per-API, or per-operation. The `<base />` element controls parent-scope policy insertion order.
- **Advanced policies** provide: `<choose>` (conditional logic), `<forward-request>` (backend forwarding), `<limit-concurrency>` (cap concurrent requests; 429 on overflow), `<log-to-eventhub>` (stream telemetry to Azure Event Hubs), `<mock-response>` (stub responses; prefers examples > schemas > empty), `<retry>` (configurable backoff), `<return-response>` (abort pipeline with custom response).
- **Subscription keys** are the primary access control mechanism; passed as `Ocp-Apim-Subscription-Key` header or `subscription-key` query string; scoped to All APIs / Single API / Product; every subscription has primary + secondary keys for zero-downtime rotation.
- **Certificate-based auth** provides TLS mutual authentication; enforced via inbound policies checking thumbprint, CA, subject, and/or expiration; Consumption tier requires explicit enablement; multi-partner scenarios upload certificates to the API Management store.

**Contradictions found:** None. Content is consistent across all 6 units.
