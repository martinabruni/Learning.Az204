---
title: "Feature Flags"
type: concept
tags: [feature-flags, feature-management, app-configuration, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-app-configuration_4-app-configuration-feature-management.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Feature Flags

## What They Are

Feature flags (also called feature toggles or feature switches) are a software development technique that **decouples feature release from code deployment**. A feature flag is a variable with a binary on/off state; its value determines whether a code block executes.

## Core Components

| Component | Role |
|-----------|------|
| **Feature flag** | Boolean variable controlling a code block |
| **Feature manager** | Package managing the lifecycle of all feature flags (caching, state updates) |
| **Filter** | Rule evaluating whether a flag should be on (user group, device type, geo, time window, percentage) |

## Basic Pattern

```csharp
if (featureFlag) {
    // Feature-specific code
}
```

## Flag Evaluation

When a feature flag has multiple filters:
- Filters are evaluated in order.
- First filter that enables the feature wins; flag is set to on.
- If no filter enables the feature, the flag remains off.

## Declaration in JSON (`appsettings.json`)

```json
"FeatureManagement": {
    "FeatureA": true,
    "FeatureB": false,
    "FeatureC": {
        "EnabledFor": [{
            "Name": "Percentage",
            "Parameters": { "Value": 50 }
        }]
    }
}
```

## Externalized Repository Pattern

Best practice: store feature flags in an external repository ([[azure-app-configuration]]) so they can be toggled without redeployment. This requires two components working together:
1. Application code that reads and acts on feature flags.
2. An external repository (App Configuration) that stores flag state.

## Use Cases

- **A/B testing**: Enable a feature for a percentage of users.
- **Canary releases**: Gradually roll out to user segments.
- **Kill switches**: Instantly disable a malfunctioning feature.
- **Beta programs**: Enable features for specific user groups.

## Related Pages

- [[azure-app-configuration]] – the recommended external store for feature flags
- [[app-configuration-feature-management]] – source page with full details
- [[app-configuration-keys-values]] – feature flags stored as key-values
