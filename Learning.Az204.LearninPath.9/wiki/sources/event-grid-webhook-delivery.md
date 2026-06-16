---
title: "Receive Events by Using Webhooks"
type: source
tags: [event-grid, webhook, validation, az204]
sources: [learn.microsoft.com_en-us_training_modules_azure-event-grid_6-webhook-event-delivery.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Receive Events by Using Webhooks

> [!source] learn.microsoft.com_en-us_training_modules_azure-event-grid_6-webhook-event-delivery.pdf

## Overview

Webhooks are a delivery mechanism for [[azure-event-grid]] events. When an event is ready, Event Grid POSTs an HTTP request to the configured endpoint with the event in the request body.

Event Grid requires **ownership validation** of webhook endpoints before starting delivery — to prevent malicious flooding.

## Auto-Validated Azure Services

The following Azure services validate automatically without custom code:
- Azure Logic Apps with Event Grid Connector
- Azure Automation via webhook
- Azure Functions with Event Grid Trigger

## Endpoint Validation Handshake

For all other endpoints (e.g., HTTP trigger Azure Function), the endpoint must participate in a validation handshake.

### Synchronous Handshake

1. On subscription creation, Event Grid sends a **subscription validation event**.
2. The `data` object includes a `validationCode` property.
3. The endpoint returns the `validationCode` synchronously in the HTTP response.
4. Supported in all Event Grid versions.

### Asynchronous Handshake

For third-party services (e.g., Zapier, IFTTT) that cannot respond programmatically:

- Available from API version **2018-05-01-preview** onwards.
- Event Grid sends a `validationUrl` in the subscription validation event data.
- Endpoint must return HTTP 200 to acknowledge receipt.
- Then a GET request to `validationUrl` completes the handshake.
- `validationUrl` is valid for **5 minutes**.
- If not completed within 5 minutes: subscription state → `Failed`; must recreate the subscription.

> "Using self-signed certificates for validation isn't supported. Use a signed certificate from a commercial certificate authority (CA) instead."

## Key Data Points

- Validation URL valid for 5 minutes.
- Provisioning state during pending manual validation: `AwaitingManualAction`.
- Endpoint must return HTTP 200 on the POST validation event (even in async mode).

## Related Pages

- [[azure-event-grid]] — entity page
- [[event-grid-overview]] — core concepts
- [[event-grid-delivery-retry]] — delivery reliability
- [[webhook-validation-pattern]] — concept page
