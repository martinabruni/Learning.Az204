---
title: "Azure Resource Manager"
type: entity
tags: [azure-resource-manager, azure, arm, managed-identity, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Resource Manager

## What It Is

Azure Resource Manager (ARM) is the deployment and management service for Azure. It provides a unified management layer for creating, updating, and deleting Azure resources. In the context of managed identities, ARM is the orchestrator that creates service principals and configures the Azure Instance Metadata Service (IMDS).

## Role in Managed Identity Flow

When a managed identity is requested on a VM, ARM:
1. Receives the request to enable or create the managed identity.
2. Creates a **service principal** in [[microsoft-entra-id]] for the identity.
3. Updates the **Azure Instance Metadata Service (IMDS)** identity endpoint on the VM with the service principal client ID and certificate.

ARM performs these steps for both system-assigned and user-assigned managed identities.

## Azure Instance Metadata Service (IMDS)

- Endpoint: `http://169.254.169.254/metadata/identity/oauth2/token`
- Accessible **only from within the VM** — a security boundary.
- Used by code running on the VM to request access tokens from [[microsoft-entra-id]].

## RBAC in ARM Context

To grant a managed identity access to call Azure Resource Manager APIs, use **role-based access control (RBAC)** in Microsoft Entra ID to assign the appropriate role to the service principal.

## Related Pages

- [[managed-identity]] – the identity type ARM creates and manages
- [[microsoft-entra-id]] – where service principals are created
- [[managed-identities-authentication-flow]] – full step-by-step flow involving ARM
