---
title: "Application Settings"
type: concept
tags: [configuration, environment-variables, app-service, az204]
sources: [learn.microsoft.com_en-us_training_modules_configure-web-app-settings_2-configure-application-settings.pdf]
created: 2025-01-15
updated: 2025-01-15
---

# Application Settings

## Definition

**Application settings** are name-value pairs exposed to [[azure-app-service]] apps as environment variables at startup. They provide a secure, platform-managed way to externalize configuration from code.

## Key Behaviours

- Injected as environment variables at app startup.
- Changing any setting triggers an **app restart**.
- Always **encrypted at rest**.
- Override `Web.config` / `appsettings.json` for ASP.NET and ASP.NET Core apps.
- Linux / container apps receive settings via the `--env` flag.

## Naming Rules

Allowed characters in setting names: letters, digits (0–9), `.`, `_`.

## Slot Stickiness

Settings can be marked **slot-specific** to prevent them from being swapped during a [[slot-swapping|slot swap]]. This enables different credentials or endpoints per environment (e.g. dev DB vs. production DB).

## Connection Strings

Follow the same rules. Environment variable prefix by database type:

| Type | Prefix |
|------|--------|
| SQL Server | `SQLCONNSTR_` |
| MySQL | `MYSQLCONNSTR_` |
| PostgreSQL | `POSTGRESQLCONNSTR_` |
| Custom | `CUSTOMCONNSTR_` |

## Portal Access

**Azure portal → App → Environment variables → Application settings**

## Related Pages

- [[configure-application-settings]] – source page
- [[azure-app-service]] – the platform
- [[deployment-slot]] – slot stickiness context
- [[slot-swapping]] – how settings behave during swaps
- [[general-settings]] – other configuration settings
