---
title: "Function App"
type: entity
tags: [azure-functions, function-app, deployment, az204]
sources: [learn.microsoft.com_en-us_training_modules_develop-azure-functions_2-azure-function-development-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Function App

## What It Is

A **function app** is the unit of deployment, management, and scaling for [[azure-functions]]. It provides the execution context in which individual functions run.

## Key Properties

- One or more individual functions managed, deployed, and scaled together.
- All functions in a function app share the **same pricing plan**, **deployment method**, and **runtime version**.
- Starting with Functions 2.x: all functions must be authored in the **same language**.

## Project Files

| File | Purpose |
|------|---------|
| `host.json` | App-wide configuration; affects all functions; applied equally to bindings |
| `local.settings.json` | Local development settings; never commit to source control |

### Settings by Environment

| Context | Config location |
|---------|----------------|
| Deployed to Azure | Application settings (encrypted env vars) |
| Local development | `local.settings.json` |

## Security Note

`local.settings.json` may contain secrets (connection strings). It must **never** be stored in a remote repository.

## Related Pages

- [[azure-functions]] – parent service
- [[triggers-and-bindings]] – function programming model
- [[managed-identity]] – identity for service connections
- [[explore-azure-functions-development]] – source
- [[create-triggers-and-bindings]] – source
- [[connect-functions-to-azure-services]] – source
