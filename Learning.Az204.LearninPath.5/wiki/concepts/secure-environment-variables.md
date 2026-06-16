---
title: "Secure Environment Variables"
type: concept
tags: [aci, environment-variables, security, secrets, az204]
sources: [aci-environment-variables.md]
created: 2026-06-16
updated: 2026-06-16
---

# Secure Environment Variables

Secure environment variables in [[azure-container-instances]] allow passing **sensitive configuration** (passwords, keys) to containers without exposing the values in the container's properties.

## How They Differ from Regular Variables

| Aspect | Regular | Secure |
|---|---|---|
| Visible in portal/CLI | Yes (name + value) | Name only |
| Defined using | `value` property | `secureValue` property |
| Access from container | Yes | Yes |
| Security | Exposed | Hidden |

## YAML Example

```yaml
environmentVariables:
  - name: 'NOTSECRET'
    value: 'my-exposed-value'
  - name: 'SECRET'
    secureValue: 'my-secret-value'
```

## Why Use Secure Values

- Safer than baking secrets into the container image.
- More flexible than image-embedded secrets.
- Values accessible only from within the container.

## Related Pages

- [[azure-container-instances]] – entity page
- [[aci-environment-variables]] – source page
