---
title: "Explore Azure Functions Development"
type: source
tags: [azure-functions, development, function-app, host-json, local-settings, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_2-azure-function-development-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Functions Development

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_2-azure-function-development-overview.pdf

## Overview

A **function app** is the unit of deployment and management for Azure Functions. It provides the execution context in which functions run. All functions in a function app share the same pricing plan, deployment method, and runtime version.

> [!source] learn.microsoft.com_en-us_training_modules_develop-azure-functions_2-azure-function-development-overview.pdf
> "Think of a function app as a way to organize and collectively manage your functions."

## Key Constraints

- In **Functions 2.x and later**, all functions in a function app must be authored in the **same language**.
- Develop locally using your preferred code editor; the Azure portal has limitations for editing function code directly.

## Local Development

Functions can be developed and debugged locally using the full Functions runtime. Local functions can connect to live Azure services.

## Local Project Files

Every Functions project directory contains (regardless of language):

- **`host.json`** — metadata file with configuration options affecting all functions in the function app instance. Binding configurations in `host.json` apply equally to each function. Settings can be overridden per environment via application settings.
- **`local.settings.json`** — stores app settings used only during local development. Used by local development tools. **Never commit to a remote repository** (may contain secrets such as connection strings).

### Settings Management

| Location | Config source |
|----------|--------------|
| Deployed to Azure | Application settings |
| Local development | `local.settings.json` |

### Synchronize Settings

Local settings required by the app must also be present in the deployed function app's application settings. Current settings can be downloaded from Azure to the local project.

## Key Claims

- `host.json` is the single source of truth for function app–wide runtime configuration.
- `local.settings.json` is for local use only; never stored in source control.
- Function app = unit of deployment, scaling, and management.

## Related Pages

- [[azure-functions]] – entity page
- [[function-app]] – entity page
- [[triggers-and-bindings]] – concept
- [[create-triggers-and-bindings]] – next source
- [[connect-functions-to-azure-services]] – source
