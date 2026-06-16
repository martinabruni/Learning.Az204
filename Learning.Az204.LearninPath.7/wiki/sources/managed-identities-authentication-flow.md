---
title: "Managed Identities Authentication Flow"
type: source
tags: [managed-identity, authentication, azure-vm, entra-id, az204, security]
sources: [learn.microsoft.com_en-us_training_modules_implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Managed Identities Authentication Flow

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf

## Overview

This unit details the step-by-step authentication flows for both [[managed-identity|system-assigned and user-assigned managed identities]] when used with Azure Virtual Machines. The flows show how a service principal is created, how credentials are provisioned, and how access tokens are obtained.

## System-Assigned Managed Identity Flow (Azure VM)

1. [[azure-resource-manager]] receives a request to enable the system-assigned managed identity on a VM.
2. Azure Resource Manager creates a **service principal** in [[microsoft-entra-id]] for the VM identity (in the tenant trusted by the subscription).
3. Azure Resource Manager configures the identity on the VM by updating the **Azure Instance Metadata Service (IMDS)** identity endpoint with the service principal client ID and certificate.
4. Use the service principal to grant VM access to Azure resources — via RBAC for ARM calls, or via Key Vault access policy for [[azure-key-vault]] calls.
5. Code running on the VM requests a token from the IMDS endpoint (accessible only from within the VM):
   - `http://169.254.169.254/metadata/identity/oauth2/token`
6. [[microsoft-entra-id]] returns a **JSON Web Token (JWT)** access token using the client ID and certificate from step 3.
7. Code sends the access token on calls to services that support Microsoft Entra authentication.

## User-Assigned Managed Identity Flow (Azure VM)

1. Azure Resource Manager receives a request to create a user-assigned managed identity.
2. Azure Resource Manager creates a service principal in Microsoft Entra ID for the user-assigned identity.
3. Azure Resource Manager configures the user-assigned identity on the VM by updating the IMDS identity endpoint with the service principal client ID and certificate.
4. Grant the user-assigned identity access to Azure resources (RBAC for ARM, Key Vault access policy for Key Vault).
5. Code on the VM requests a token from IMDS: `http://169.254.169.254/metadata/identity/oauth2/token`

> [!source] learn.microsoft.com_en-us_training_modules_implement-managed-identities_3-managed-identities-auzre-virtual-machines.pdf
> "You can also do this step before step 3." (granting permissions before assigning identity)

6. Microsoft Entra ID returns a JWT access token.
7. Code sends the access token to services supporting Microsoft Entra authentication.

## Key Claims

- The IMDS endpoint (`http://169.254.169.254/metadata/identity/oauth2/token`) is **only accessible from within the VM** — this is a security boundary.
- Both flows result in a **JWT access token** issued by Microsoft Entra ID.
- The same token acquisition pattern applies to all Azure resources that support Microsoft Entra authentication.

## Related Pages

- [[managed-identity]] – entity page
- [[microsoft-entra-id]] – identity provider
- [[azure-resource-manager]] – orchestrates identity creation
- [[azure-key-vault]] – common target for managed identity access
- [[explore-managed-identities]] – types and characteristics
- [[configure-managed-identities]] – CLI configuration
- [[acquire-access-token]] – SDK-level token acquisition
