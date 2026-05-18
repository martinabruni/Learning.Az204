---
title: "Configure Application Settings"
type: source
tags: [app-service, configuration, environment-variables, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_2-configure-application-settings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Configure Application Settings

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_2-configure-application-settings.pdf

## Overview

[[application-settings]] in [[azure-app-service]] are environment variables injected at app startup.

## Key Claims

- For Linux / custom containers: settings passed via `--env` flag.
- For ASP.NET/Core: App Service overrides `Web.config` or `appsettings.json`.
- Settings are **always encrypted at rest**.
- Name characters allowed: letters, digits, `.`, `_`.
- Any change to settings triggers an **app restart**.
- Accessible via **Environment variables → Application settings** in the portal.

> [!source] learn.microsoft.com_en-us_training_modules_configure-web-app-settings_2-configure-application-settings.pdf
> "App settings are always encrypted when stored (encrypted-at-rest)."

## Slot Stickiness

When using [[deployment-slot|deployment slots]], each setting can be:
- **Swappable** (default): moves with the slot content during [[slot-swapping|swap]].
- **Slot-specific (sticky)**: stays pinned to its slot, even after swap.

## Bulk Editing

Use the **Advanced edit** button to manage multiple settings as JSON.

## Connection Strings

Follow the same override and slot-stickiness pattern. Environment variable prefix by type:

| Type | Prefix |
|------|--------|
| SQL Server | `SQLCONNSTR_` |
| MySQL | `MYSQLCONNSTR_` |
| PostgreSQL | `POSTGRESQLCONNSTR_` |
| Custom | `CUSTOMCONNSTR_` |

## Related Pages

- [[configure-web-app-settings-introduction]] – module intro
- [[deployment-slot]] – slot stickiness behaviour
- [[slot-swapping]] – how swaps interact with settings
- [[application-settings]] – concept deep-dive
