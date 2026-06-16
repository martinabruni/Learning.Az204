---
title: "Configure Managed Identities"
type: source
tags: [managed-identity, azure-cli, azure-vm, az204, security]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_4-configure-managed-identities.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Configure Managed Identities

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_4-configure-managed-identities.pdf

## Overview

[[managed-identity|Managed identities]] can be configured on Azure Virtual Machines at creation time or after creation. This unit covers the Azure CLI commands for both [[managed-identity|system-assigned and user-assigned]] identities, and lists Azure SDK samples.

## System-Assigned Managed Identity

Required role: **Virtual Machine Contributor** — no other Microsoft Entra directory role assignments are needed.

### Enable during VM creation

```bash
az vm create --resource-group myResourceGroup \
    --name myVM --image win2016datacenter \
    --generate-ssh-keys \
    --assign-identity \
    --role contributor \
    --scope mySubscription \
    --admin-username azureuser \
    --admin-password myPassword12
```

Key parameter: `--assign-identity` (no value = system-assigned).

### Enable on an existing VM

```bash
az vm identity assign -g myResourceGroup -n myVm
```

## User-Assigned Managed Identity

Required roles: **Virtual Machine Contributor** AND **Managed Identity Operator**.

Enabling user-assigned identities is a **two-step process**:
1. Create the user-assigned identity.
2. Assign the identity to a virtual machine.

### Step 1: Create the identity

```bash
az identity create -g myResourceGroup -n myUserAssignedIdentity
```

### Step 2a: Assign during VM creation

```bash
az vm create \
  --resource-group <RESOURCE GROUP> \
  --name <VM NAME> \
  --image Ubuntu2204 \
  --admin-username <USER NAME> \
  --admin-password <PASSWORD> \
  --assign-identity <USER ASSIGNED IDENTITY NAME> \
  --role <ROLE> \
  --scope <SUBSCRIPTION>
```

### Step 2b: Assign to an existing VM

```bash
az vm identity assign \
    -g <RESOURCE GROUP> \
    -n <VM NAME> \
    --identities <USER ASSIGNED IDENTITY>
```

## Azure SDK Samples

| SDK | Sample |
|-----|--------|
| .NET | Manage resource from a VM enabled with managed identities |
| Java | Manage storage from a VM enabled with managed identities |
| Node.js | Create a VM with system-assigned managed identity enabled |
| Python | Create a VM with system-assigned managed identity enabled |
| Ruby | Create Azure VM with a system-assigned identity enabled |

## Key Claims

- System-assigned identity: single CLI flag `--assign-identity` on `az vm create`.
- User-assigned identity: separate `az identity create` step required first.
- Role requirement difference: user-assigned requires the additional **Managed Identity Operator** role.

## Related Pages

- [[managed-identity]] – entity page
- [[explore-managed-identities]] – types overview
- [[managed-identities-authentication-flow]] – how the identity is used
- [[acquire-access-token]] – consuming the identity in code
