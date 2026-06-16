---
title: "Query Microsoft Graph by Using SDKs"
type: source
tags: [microsoft-graph, sdk, dotnet, csharp, az204]
sources: [learn.microsoft.com_en-us_training_modules_microsoft-graph_4-microsoft-graph-sdk.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Query Microsoft Graph by Using SDKs

> [!source] learn.microsoft.com_en-us_training_modules_microsoft-graph_4-microsoft-graph-sdk.pdf

## Overview

The [[microsoft-graph-sdk|Microsoft Graph SDKs]] simplify building high-quality, efficient, and resilient applications accessing Microsoft Graph.

## Key Claims

### SDK Architecture (Two Libraries)

- **Service library** — models and request builders generated from Microsoft Graph metadata; rich and discoverable API surface.
- **Core library** — cross-cutting features: retry handling, secure redirects, transparent authentication, payload compression, paging through collections, batch requests.

### .NET NuGet Packages

| Package | Purpose |
|---------|---------|
| `Microsoft.Graph` | Models and request builders for `v1.0` endpoint (fluent API); depends on `Microsoft.Graph.Core` |
| `Microsoft.Graph.Beta` | Models and request builders for `beta` endpoint; depends on `Microsoft.Graph.Core` |
| `Microsoft.Graph.Core` | Core library for all Microsoft Graph calls |

Note: code samples based on **version 5.65** of the .NET SDK.

### Creating a Graph Client

Use a single `GraphServiceClient` instance for the lifetime of the application. Authentication is handled by an authentication provider.

```csharp
var scopes = new[] { "User.Read" };
var tenantId = "common"; // or specific tenant ID
var clientId = "YOUR_CLIENT_ID";

var options = new TokenCredentialOptions
{
    AuthorityHost = AzureAuthorityHosts.AzurePublicCloud
};

Func<DeviceCodeInfo, CancellationToken, Task> callback = (code, cancellation) => {
    Console.WriteLine(code.Message);
    return Task.FromResult(0);
};

var deviceCodeCredential = new DeviceCodeCredential(callback, tenantId, clientId, options);
var graphClient = new GraphServiceClient(deviceCodeCredential, scopes);
```

### Common Operations

**Read a single entity (GET):**
```csharp
var user = await graphClient.Me.GetAsync();
```

**Retrieve a filtered list:**
```csharp
var messages = await graphClient.Me.Messages
    .GetAsync(requestConfig => {
        requestConfig.QueryParameters.Select = ["subject", "sender"];
        requestConfig.QueryParameters.Filter = "subject eq 'Hello world'";
    });
```

**Delete an entity (DELETE):**
```csharp
await graphClient.Me.Messages[messageId].DeleteAsync();
```

**Create a new entity (POST):**
```csharp
var calendar = new Calendar { Name = "Volunteer" };
var newCalendar = await graphClient.Me.Calendars.PostAsync(calendar);
```

## Related Pages

- [[microsoft-graph]] – entity page
- [[microsoft-graph-rest-api]] – REST approach
- [[microsoft-graph-best-practices]] – best practices
- [[msal]] – provides authentication tokens used by the SDK
