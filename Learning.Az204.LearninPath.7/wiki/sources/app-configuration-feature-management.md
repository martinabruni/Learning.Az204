---
title: "Manage Application Features"
type: source
tags: [app-configuration, feature-flags, feature-management, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_4-app-configuration-feature-management.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Manage Application Features

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_4-app-configuration-feature-management.pdf

## Overview

Feature management is a modern practice that **decouples feature release from code deployment**, enabling real-time changes to feature availability without redeploying.

## Core Concepts

| Term | Definition |
|------|-----------|
| **Feature flag** | A variable with binary on/off state; controls whether a code block executes |
| **Feature manager** | Application package managing the lifecycle of all feature flags (caching, state updates) |
| **Filter** | Rule for evaluating a feature flag's state (e.g., user group, browser type, geographic location, time window) |

## Feature Flag Usage Pattern

```csharp
if (featureFlag) {
    // Run the following code
}
```

Can be set statically or rule-based:

```csharp
bool featureFlag = true;                // static
bool featureFlag = isBetaUser();        // rule-based
```

## Feature Flag Declaration

Each feature flag has:
- A **name**
- One or more **filters** that evaluate whether the flag is on

When multiple filters exist, the list is traversed in order until one enables the feature. If no filter enables it, the flag is off.

### JSON Declaration Example (`appsettings.json`)

```json
"FeatureManagement": {
    "FeatureA": true,
    "FeatureB": false,
    "FeatureC": {
        "EnabledFor": [
            {
                "Name": "Percentage",
                "Parameters": {
                    "Value": 50
                }
            }
        ]
    }
}
```

## Feature Flag Repository

- Feature flags should be **externalized** from application code so their states can change without code redeployment.
- [[azure-app-configuration]] is designed to be a **centralized repository** for feature flags.

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_4-app-configuration-feature-management.pdf
> "Azure App Configuration is designed to be a centralized repository for feature flags. You can use it to define different kinds of feature flags and manipulate their states quickly and confidently."

## Effective Implementation Requirements

1. An application that uses feature flags.
2. A separate repository (like App Configuration) that stores the flags and their states.

## Key Claims

- Feature flags enable **A/B testing**, gradual rollouts, and kill-switch patterns without code changes.
- The feature manager supports `appsettings.json` as a local configuration source for feature flags.
- A `Percentage` filter (FeatureC example) enables a feature for a percentage of requests/users.

## Related Pages

- [[azure-app-configuration]] – entity page
- [[feature-flags]] – concept page
- [[explore-app-configuration]] – service overview
- [[app-configuration-keys-values]] – underlying key-value data model
- [[secure-app-configuration-data]] – securing the App Configuration store
