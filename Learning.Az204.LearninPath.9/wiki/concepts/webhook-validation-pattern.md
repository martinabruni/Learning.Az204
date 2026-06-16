---
title: "Webhook Validation Pattern (Event Grid)"
type: concept
tags: [event-grid, webhook, validation, security, az204]
sources: [event-grid-webhook-delivery.md]
created: 2026-06-16
updated: 2026-06-16
---

# Webhook Validation Pattern (Event Grid)

[[azure-event-grid]] requires webhook endpoints to **prove ownership** before receiving events — preventing malicious actors from directing event floods to arbitrary URLs.

## Auto-Validated Services

No custom code needed:
- Azure Logic Apps (Event Grid Connector)
- Azure Automation (webhook)
- Azure Functions (Event Grid Trigger)

## Validation Handshakes

### Synchronous Handshake

1. On subscription creation, Event Grid sends a **subscription validation event**.
2. Event data contains a `validationCode`.
3. Endpoint extracts and returns the code synchronously in the HTTP response.
4. Supported in all Event Grid API versions.

### Asynchronous (Manual) Handshake

Used when the endpoint cannot respond programmatically (e.g., Zapier, IFTTT).

Available from API version **2018-05-01-preview**:

1. Event data contains a `validationUrl`.
2. Endpoint must return HTTP 200 to acknowledge receipt.
3. Operator performs a GET request to `validationUrl` within 5 minutes.
4. On success: subscription state → active.
5. On timeout: subscription state → `Failed`; must recreate subscription.

## Key Constraints

- `validationUrl` valid for **5 minutes**.
- Endpoint must always return HTTP 200 on the validation POST.
- **Self-signed certificates not supported**; must use a certificate from a commercial CA.

## Related Pages

- [[azure-event-grid]] — entity
- [[event-grid-webhook-delivery]] — source page
- [[event-grid-security]] — broader security concept
