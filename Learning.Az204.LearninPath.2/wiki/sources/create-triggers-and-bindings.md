---
title: "Create Triggers and Bindings"
type: source
tags: [azure-functions, triggers, bindings, function-json, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_3-create-triggers-bindings.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Create Triggers and Bindings

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_3-create-triggers-bindings.pdf

## Overview

- A **trigger** defines how a function is invoked. Every function must have **exactly one trigger**. Triggers carry associated data (often the function payload).
- A **binding** is a declarative way to connect another resource to the function. Bindings can be input, output, or both. Data from bindings is provided as function parameters.
- Bindings are **optional**; a function may have zero, one, or multiple input/output bindings.
- Triggers and bindings eliminate hardcoded access to other services.

## Local Testing of Triggers and Bindings

- **HTTP triggers**: call `http://localhost/` on the local machine.
- **Non-HTTP triggers options**:
  1. Use connection strings targeting live Azure services in `local.settings.json` `Values` array.
  2. Use the **Azurite emulator** for storage-based triggers (Queue Storage, Blob Storage, Table Storage).
  3. Manually invoke using special administrator endpoints.

## Trigger and Binding Definitions by Language

| Language | Configuration approach |
|----------|----------------------|
| C# class library | C# attributes on methods/parameters (in-process or isolated worker) |
| Java | Java annotations on methods/parameters |
| JavaScript/TypeScript v4 | Code-first using `@azure/functions`; v3: `function.json` |
| Python v2 | Decorators; v1: `function.json` |
| PowerShell | `function.json` |

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_3-create-triggers-bindings.pdf
> "In modern models (Node.js v4 and Python v2), you author trigger and binding configuration in code and the runtime generates the corresponding function.json. Older models (Node.js v3, Python v1, PowerShell) use function.json directly. You can't mix programming models within the same function app."

## function.json Structure

For legacy models (Node.js v3, Python v1, PowerShell), `function.json` contains a `bindings` array:

```json
{
  "disabled": false,
  "bindings": [
    {
      "type": "httpTrigger",
      "direction": "in",
      "name": "req",
      "authLevel": "function",
      "methods": ["get", "post"]
    },
    {
      "type": "queue",
      "direction": "out",
      "name": "outqueue",
      "queueName": "outqueue",
      "connection": "AzureWebJobsStorage"
    }
  ]
}
```

- Trigger: `direction` is always `in`.
- Input bindings: `direction` is `in`.
- Output bindings: `direction` is `out`.
- Some bindings support `inout` (Advanced editor only in portal).

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_3-create-triggers-bindings.pdf
> "Disabling a function via the disabled property in function.json is legacy behavior. Prefer using the app setting `AzureWebJobs.<FunctionName>.Disabled=true`."

## dataType Property (Dynamic Languages)

For dynamically-typed languages (JavaScript v3, PowerShell), use `dataType` in `function.json`:
- `binary`, `stream`, `string`

## Code Examples

### C# Isolated Worker
Uses `[HttpTrigger]` and `[QueueOutput]` attributes; no `function.json` needed.

### Node.js v4
Uses `@azure/functions` library; bindings configured in code via `output.storageQueue()` and `app.http()`.

### Python v2
Uses `@app.route()` and `@app.queue_output()` decorators; runtime generates `function.json`.

## Key Claims

- Every function has exactly one trigger.
- Modern models (Node.js v4, Python v2) generate `function.json` from code — do not edit it directly in the portal.
- You cannot mix programming models within the same function app.
- C# and Java do not use `function.json` for binding definitions and cannot be created/edited in the Azure portal.

## Related Pages

- [[azure-functions]] – entity
- [[function-app]] – entity
- [[triggers-and-bindings]] – concept
- [[explore-azure-functions-development]] – previous source
- [[connect-functions-to-azure-services]] – next source
