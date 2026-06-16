---
title: "Manage Revisions and Secrets in Azure Container Apps"
type: source
tags: [container-apps, aca, revisions, secrets, key-vault, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_6-container-apps-revisions-secrets.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Manage Revisions and Secrets in Azure Container Apps

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_6-container-apps-revisions-secrets.pdf

## Overview

[[azure-container-apps]] implements container app versioning through **revisions** and provides secure secret management at the application level.

## Revisions

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_6-container-apps-revisions-secrets.pdf
> "A revision is an immutable snapshot of a container app version."

- New revisions are created when **revision-scope changes** are made.
- You can control which revisions are **active** and how **external traffic is routed** between them.
- Revision names are used in the revision's URL.
- Customize revision name by setting the **revision suffix** (e.g., `album-api--1st-revision`).

### Update a Container App

```bash
az containerapp update \
    --name <APPLICATION_NAME> \
    --resource-group <RESOURCE_GROUP_NAME> \
    --image <IMAGE_NAME>
```

### List Revisions

```bash
az containerapp revision list \
    --name <APPLICATION_NAME> \
    --resource-group <RESOURCE_GROUP_NAME> \
    -o table
```

## Secrets

- Secrets are scoped to the **application level**, not to any specific revision.
- Adding, removing, or changing secrets does **not generate new revisions**.
- Each revision can reference one or more secrets; multiple revisions can share secrets.
- Updated/deleted secrets do **not automatically affect existing revisions**.
- To respond to secret changes: deploy a new revision or restart an existing revision.
- **Best practice**: before deleting a secret, deploy a new revision that doesn't reference it, then deactivate old revisions.

### Defining Secrets

```bash
az containerapp create \
    --resource-group "my-resource-group" \
    --name queuereader \
    --environment "my-environment-name" \
    --image demos/queuereader:v1 \
    --secrets "queue-connection-string=$CONNECTION_STRING"
```

### Referencing Secrets in Environment Variables

Use `secretref:` prefix:

```bash
--env-vars "QueueName=myqueue" "ConnectionString=secretref:queue-connection-string"
```

### Azure Key Vault Integration

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_6-container-apps-revisions-secrets.pdf
> "Container Apps supports native Azure Key Vault integration. Enable managed identity in the container app, grant the identity the Key Vault Secrets User role, and define secrets as Key Vault references using the secret's URI."

- ACA automatically retrieves and refreshes Key Vault secret values.

## Related Pages

- [[azure-container-apps]] – entity page
- [[azure-key-vault]] – entity page
- [[container-app-revisions]] – concept page
- [[aca-explore]] – ACA overview source
- [[aca-containers]] – containers source
