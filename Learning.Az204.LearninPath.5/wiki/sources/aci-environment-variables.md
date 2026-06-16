---
title: "Set Environment Variables in Container Instances"
type: source
tags: [aci, environment-variables, secure-values, az204]
sources: [learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_5-set-environment-variables-azure-container-instances.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Set Environment Variables in Container Instances

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_5-set-environment-variables-azure-container-instances.pdf

## Overview

Environment variables in [[azure-container-instances]] enable dynamic configuration of the application or script run by the container. They are equivalent to the `--env` argument in `docker run`.

## Key Claims

- Environment variables are passed via `--environment-variables` in the Azure CLI.
- ACI supports **secure values** for both Windows and Linux containers.
- Secure environment variables are **not visible** in container properties (portal or CLI) — only the name is shown, not the value.
- Secure values are more flexible and safer than baking secrets into a container image.

## Setting Regular Environment Variables

```bash
az container create \
    --resource-group myResourceGroup \
    --name mycontainer2 \
    --image mcr.microsoft.com/azuredocs/aci-wordcount:latest \
    --restart-policy OnFailure \
    --environment-variables 'NumWords'='5' 'MinLength'='8'
```

> On Windows Command Prompt, use double-quotes: `--environment-variables "NumWords"="5" "MinLength"="8"`

## Secure Environment Variables (YAML)

Use `secureValue` instead of `value` in YAML to hide sensitive data:

```yaml
environmentVariables:
  - name: 'NOTSECRET'
    value: 'my-exposed-value'
  - name: 'SECRET'
    secureValue: 'my-secret-value'
```

Deploy with:

```bash
az container create --resource-group myResourceGroup \
    --file secure-env.yaml
```

## Data Points

- Secure values: visible name, **hidden value** in Azure portal and Azure CLI output.

## Related Pages

- [[azure-container-instances]] – entity page
- [[secure-environment-variables]] – concept page
- [[aci-overview]] – ACI overview source
- [[aci-restart-policies]] – restart policies source
