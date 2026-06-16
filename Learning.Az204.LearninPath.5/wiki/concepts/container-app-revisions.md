---
title: "Container App Revisions"
type: concept
tags: [container-apps, aca, revisions, blue-green, traffic-splitting, az204]
sources: [aca-revisions-secrets.md, aca-explore.md]
created: 2026-06-16
updated: 2026-06-16
---

# Container App Revisions

Revisions are the **versioning mechanism** in [[azure-container-apps]]. Each revision is an **immutable snapshot** of a container app version.

## Key Properties

- Created automatically when **revision-scope changes** are deployed.
- Identified by **revision name** (used in revision URL).
- Default naming: `<app-name>--<random-suffix>`.
- Customizable with a **revision suffix**.
- Multiple revisions can be active simultaneously.

## Traffic Routing

- External traffic can be routed to each active revision by percentage.
- Enables **Blue/Green deployments** and **A/B testing**.

## Secrets and Revisions

- Adding, removing, or changing secrets does **not generate new revisions**.
- Secrets are **application-scoped**, not revision-scoped.
- Multiple revisions can reference the same secret.
- Secret updates don't automatically affect existing revisions — must redeploy or restart.

## CLI Commands

```bash
# Update a container app (may create new revision)
az containerapp update \
    --name <APP_NAME> \
    --resource-group <RG> \
    --image <IMAGE>

# List all revisions
az containerapp revision list \
    --name <APP_NAME> \
    --resource-group <RG> \
    -o table
```

## Related Pages

- [[azure-container-apps]] – entity page
- [[aca-revisions-secrets]] – source page
- [[aca-explore]] – overview source
