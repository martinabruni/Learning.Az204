---
title: "Azure Event Hubs"
type: entity
tags: [event-hubs, azure, logging, streaming, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_5-create-advanced-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Event Hubs

## What It Is

Azure Event Hubs is a big data streaming platform and event ingestion service capable of receiving and processing millions of events per second.

## Relevance to API Management

In the context of [[azure-api-management]], Event Hubs is used as a **log target** via the `log-to-eventhub` policy. API Management defines a Logger entity pointing to an Event Hub, and the policy streams selected request/response context information to it for online or offline analysis.

## Usage in APIM

```xml
<log-to-eventhub logger-id="id of the logger entity"
                 partition-id="index of the partition"
                 partition-key="value used for partition assignment">
  Expression returning a string to be logged
</log-to-eventhub>
```

- `logger-id` refers to a Logger entity configured in the API Management instance.
- Supports both partition-id (fixed partition) and partition-key (dynamic assignment) routing.

## Related Pages

- [[azure-api-management]] – service that uses Event Hubs for logging
- [[apim-advanced-policies]] – the `log-to-eventhub` policy
- [[create-advanced-policies]] – source page with policy details

## Source References

- [[create-advanced-policies]]
