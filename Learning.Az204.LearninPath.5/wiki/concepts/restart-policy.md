---
title: "Container Restart Policy (ACI)"
type: concept
tags: [aci, restart-policy, run-once, az204]
sources: [aci-restart-policies.md]
created: 2026-06-16
updated: 2026-06-16
---

# Container Restart Policy

Restart policies in [[azure-container-instances]] control what happens when a container's process exits. This enables ACI to be used as an efficient **run-once task platform**.

## Policy Options

| Policy | Behavior | Use Case |
|---|---|---|
| `Always` | Always restart (default) | Long-running services |
| `Never` | Never restart; run at most once | Batch/one-shot tasks |
| `OnFailure` | Restart only on non-zero exit code | Tasks that should retry on error |

## Billing Implication

ACI is billed **by the second** — stopping containers when tasks complete (using `Never` or `OnFailure`) minimizes costs.

## Terminated Status

When ACI stops a container with `Never` or `OnFailure` policy after completion, the container status is set to **Terminated**.

## CLI Usage

```bash
az container create \
    --restart-policy OnFailure
```

## Related Pages

- [[azure-container-instances]] – entity page
- [[aci-restart-policies]] – source page
