---
title: "Run Containerized Tasks with Restart Policies"
type: source
tags: [aci, restart-policy, container-instances, az204]
sources: [learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_4-run-containerized-tasks-restart-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Run Containerized Tasks with Restart Policies

> [!source] learn.microsoft.com_en-us_training_modules_create-run-container-images-azure-container-instances_4-run-containerized-tasks-restart-policies.pdf

## Overview

[[azure-container-instances]] provides a compelling platform for **run-once tasks** such as build, test, and image rendering jobs. Container instances are **billed by the second**, so you pay only for active compute.

## Key Claims

- Restart policies allow containers to be stopped automatically when their processes complete.
- Billing is per-second — cost is minimized by stopping containers when done.

## Restart Policy Options

| Policy | Behavior |
|---|---|
| `Always` | Containers always restart. **Default** when no policy is specified. |
| `Never` | Containers never restart. Run at most once. |
| `OnFailure` | Containers restart only when the process exits with a **nonzero exit code**. Run at least once. |

## Specifying a Restart Policy

Use the `--restart-policy` parameter with `az container create`:

```bash
az container create \
    --resource-group myResourceGroup \
    --name mycontainer \
    --image mycontainerimage \
    --restart-policy OnFailure
```

## Run to Completion

- When ACI stops a container whose policy is `Never` or `OnFailure`, the container status is set to **Terminated**.

## Related Pages

- [[azure-container-instances]] – entity page
- [[restart-policy]] – concept page
- [[aci-overview]] – ACI overview source
