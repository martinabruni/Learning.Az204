---
title: "Triggers and Bindings"
type: concept
tags: [azure-functions, triggers, bindings, function-json, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_3-create-triggers-bindings.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Triggers and Bindings

## Definitions

- **Trigger**: defines how a function is invoked. Every [[azure-functions|Azure Function]] must have **exactly one trigger**. Triggers carry associated data (often the function payload). Trigger `direction` is always `in`.
- **Binding**: a declarative connection to another resource. Can be input (`in`), output (`out`), or both (`inout`). Bindings are **optional**; a function may have zero or many. Data is provided as function parameters (input) or via return value (output).

## Why Use Them

Triggers and bindings eliminate hardcoded access to other services. The function receives data in parameters and sends data via return values — no explicit SDK calls needed.

## Configuration by Language

| Language | Method |
|----------|--------|
| C# class library | C# attributes (in-process or isolated worker) |
| Java | Java annotations |
| JavaScript/TypeScript v4 | `@azure/functions` in code |
| JavaScript/TypeScript v3 | `function.json` |
| Python v2 | Decorators |
| Python v1 | `function.json` |
| PowerShell | `function.json` |

## function.json (Legacy Models)

For Node.js v3, Python v1, PowerShell — triggers and bindings are declared in a JSON `bindings` array with `type`, `direction`, and `name` properties:

```json
{
  "bindings": [
    { "type": "httpTrigger", "direction": "in", "name": "req", "authLevel": "function", "methods": ["get","post"] },
    { "type": "queue", "direction": "out", "name": "outqueue", "queueName": "outqueue", "connection": "AzureWebJobsStorage" }
  ]
}
```

## Binding Direction Summary

| Direction | Used for |
|-----------|---------|
| `in` | Triggers (always) and input bindings |
| `out` | Output bindings |
| `inout` | Special bidirectional bindings (Advanced editor only) |

## dataType Property

For dynamically-typed languages (JavaScript v3, PowerShell), use `dataType` in `function.json`: `binary`, `stream`, or `string`.

## Supported Trigger Types

Timer, HTTP/WebHook, Azure Storage queues/blobs, Azure Service Bus queues/topics, Azure Cosmos DB, Azure Event Hubs, Azure Event Grid.

## Key Rules

- Cannot mix programming models within the same [[function-app]].
- Modern models (Node.js v4, Python v2) generate `function.json` automatically — do not edit directly in portal.
- C# and Java cannot be created or edited in the Azure portal (they don't use `function.json` for binding definitions).
- Disabling a function: prefer app setting `AzureWebJobs.<FunctionName>.Disabled=true` over legacy `"disabled": true` in `function.json`.

## Local Testing

- HTTP triggers: `http://localhost/`
- Storage-based triggers: use **Azurite emulator**
- Non-HTTP triggers: use connection strings targeting live Azure services, or administrator endpoints

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – unit of deployment
- [[create-triggers-and-bindings]] – source
- [[explore-azure-functions-development]] – source
- [[functions-hosting-plans]] – how triggers affect scaling
