---
title: "App Configuration Keys and Values"
type: source
tags: [app-configuration, azure, key-value, labels, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_3-keys-values.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# App Configuration Keys and Values

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_3-keys-values.pdf

## Overview

[[azure-app-configuration]] stores configuration data as **key-value pairs**. Keys are case-sensitive, unicode-based strings; values are also unicode strings.

## Keys

- Keys serve as names for key-value pairs.
- Organized using hierarchical namespaces with character delimiters (`/` or `:`).
- App Configuration treats keys as a whole — does not parse structure.
- **Case-sensitive**: `app1` and `App1` are distinct keys.
- **Reserved characters**: `*`, `,`, `\` — must be escaped with `\{Reserved Character}`.
- Combined size limit: **10,000 characters** per key-value pair (including key, value, and all attributes).

### Key Namespace Example (ASP.NET)

```
AppName:Service1:ApiEndpoint
AppName:Service2:ApiEndpoint
```

### Flat vs. Hierarchical Keys

| Approach | Advantages |
|----------|-----------|
| Flat | Simple |
| **Hierarchical** (recommended) | Easier to read, manage, and query; delimiters act as logical separators |

## Label Keys

- Key-values can have an optional **label** attribute.
- A key + label combination forms a unique identifier.
- Default: no label (reference with `\0`, URL encoded as `%00`).
- Common use: **environment-specific** variants of the same key:

```
Key = AppName:DbEndpoint & Label = Test
Key = AppName:DbEndpoint & Label = Staging
Key = AppName:DbEndpoint & Label = Production
```

## Version Key Values

- App Configuration does **not** auto-version key values.
- Use labels as a versioning strategy (e.g., application version number or Git commit ID).

## Values

- Unicode strings.
- Optional user-defined `content-type` attribute per value (e.g., for encoding scheme metadata).
- **Encrypted at rest and in transit**.

## Key Claim

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_3-keys-values.pdf
> "App Configuration isn't a replacement solution for Azure Key Vault. Don't store application secrets in it."

## Related Pages

- [[azure-app-configuration]] – entity page
- [[explore-app-configuration]] – service overview
- [[app-configuration-feature-management]] – feature flags built on key-value pairs
- [[azure-key-vault]] – for secrets (not to be stored in App Configuration)
