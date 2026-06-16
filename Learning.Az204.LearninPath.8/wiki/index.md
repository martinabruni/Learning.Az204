---
title: "Wiki Index – AZ-204 Learning Path 8: Azure API Management"
type: synthesis
tags: [index, az204, api-management]
sources: [api-management-overview.md, api-gateways.md, api-management-policies.md, create-advanced-policies.md, secure-access-api-subscriptions.md, secure-access-api-certificates.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 8: Azure API Management

This wiki is built from 6 PDFs in `raw/`, covering one Microsoft Learn module on Azure API Management (units 2–7 of the `explore-api-management` module).
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-api-management]] | Fully managed Azure service for publishing, securing, and monitoring APIs |
| [[azure-event-hubs]] | Event ingestion service used as a log target via the `log-to-eventhub` policy |

---

## Concepts

| Page | Summary |
|------|---------|
| [[apim-gateway]] | API gateway (data plane/runtime): reverse proxy that routes, transforms, and secures API traffic |
| [[apim-policies]] | XML policy pipeline with inbound, backend, outbound, and on-error sections; supports C# expressions |
| [[apim-advanced-policies]] | Advanced policy statements: choose, forward-request, limit-concurrency, log-to-eventhub, mock-response, retry, return-response |
| [[apim-products]] | Named bundles of APIs surfaced to developers; Open or Protected; linked to subscription scopes |
| [[apim-subscriptions]] | Subscription key pairs (primary + secondary) scoped to All APIs, Single API, or Product |
| [[apim-certificates]] | TLS mutual auth via inbound policies; checks thumbprint, CA, subject, and expiration |
| [[tls-mutual-auth]] | Protocol pattern where both client and server authenticate with certificates |

---

## Sources — Module: Explore API Management

| Page | PDF |
|------|-----|
| [[api-management-overview]] | `explore-api-management_2-api-management-overview.pdf` |
| [[api-gateways]] | `explore-api-management_3-api-gateways.pdf` |
| [[api-management-policies]] | `explore-api-management_4-api-management-policies.pdf` |
| [[create-advanced-policies]] | `explore-api-management_5-create-advanced-policies.pdf` |
| [[secure-access-api-subscriptions]] | `explore-api-management_6-secure-access-api-subscriptions.pdf` |
| [[secure-access-api-certificates]] | `explore-api-management_7-secure-access-api-certificates.pdf` |

---

## Page Counts

- Sources: 6
- Entities: 2
- Concepts: 7
- **Total wiki pages: 15** (plus this index and log.md)
