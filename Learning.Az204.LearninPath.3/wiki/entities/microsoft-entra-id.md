---
title: "Microsoft Entra ID"
type: entity
tags: [entra-id, authentication, identity, rbac, azure, az204]
sources: [learn.microsoft.com_en-us_training_modules_work-azure-blob-storage_3-create-client-object.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Microsoft Entra ID

## What It Is

Microsoft Entra ID (formerly Azure Active Directory) is Microsoft's cloud-based identity and access management service. In the context of Azure Blob Storage SDK development, it is used to authenticate client applications via `DefaultAzureCredential`.

## Role in Blob Storage SDK

- The .NET Blob Storage SDK uses `DefaultAzureCredential` to authenticate via a Microsoft Entra **security principal**.
- The authentication process obtains an **access token** that is passed as a credential when the client object is instantiated.
- The credential persists throughout the client lifetime.
- The security principal must be assigned an appropriate **Azure RBAC role** that grants access to blob data (e.g., Storage Blob Data Contributor, Storage Blob Data Reader).

## DefaultAzureCredential

- Part of the `Azure.Identity` package.
- Tries multiple credential types in sequence: environment variables, managed identity, Visual Studio, Azure CLI, etc.
- Simplifies authentication across different environments (local dev, production).

```csharp
using Azure.Identity;
// DefaultAzureCredential automatically finds the right auth method
new DefaultAzureCredential()
```

## Related Pages

- [[create-client-object]] – source: how DefaultAzureCredential is used in SDK
- [[azure-blob-storage-sdk]] – concept: .NET client library
- [[azure-blob-storage]] – entity: the service being accessed
