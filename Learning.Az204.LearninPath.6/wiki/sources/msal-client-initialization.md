---
title: "Initialize Client Applications (MSAL.NET)"
type: source
tags: [msal, msal-net, client-applications, initialization, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_3-initialize-client-applications.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Initialize Client Applications (MSAL.NET)

> [!source] learn.microsoft.com_en-us_training_modules_implement-authentication-by-using-microsoft-authentication-library_3-initialize-client-applications.pdf

## Overview

MSAL.NET 3.x uses application builders to instantiate applications: `PublicClientApplicationBuilder` and `ConfidentialClientApplicationBuilder`.

## Key Claims

### Prerequisites for Initialization

Information needed from Azure portal after app registration:
- **Application (client) ID** — a GUID string.
- **Directory (tenant) ID** — used for single-tenant or multi-tenant configuration.
- **Authority** — identity provider URL (instance) + sign-in audience (tenant ID or domain). Collectively called the authority.
- **Client credentials** (confidential apps only) — application secret string or `X509Certificate2` certificate.
- **Redirect URI** — where the identity provider sends the security token back.

### Code Examples

**Public client (users in Azure public cloud):**
```csharp
IPublicClientApplication app =
    PublicClientApplicationBuilder.Create(clientId).Build();
```

**Confidential client (web app with client secret):**
```csharp
IConfidentialClientApplication app =
    ConfidentialClientApplicationBuilder.Create(clientId)
        .WithClientSecret(clientSecret)
        .WithRedirectUri(redirectUri)
        .Build();
```

**Public client with authority and redirect URI:**
```csharp
IPublicClientApplication app =
    PublicClientApplicationBuilder.Create(client_id)
        .WithAuthority(AzureCloudInstance.AzurePublic, tenant_id)
        .WithRedirectUri("http://localhost")
        .Build();
```

### Builder Modifiers (common to both types)

| Modifier | Description |
|----------|-------------|
| `.WithAuthority()` | Sets the default authority (Azure Cloud, audience, tenant ID/domain, or URI) |
| `.WithTenantId(string)` | Overrides tenant ID |
| `.WithClientId(string)` | Overrides client ID |
| `.WithRedirectUri(string)` | Overrides the default redirect URI |
| `.WithComponent(string)` | Sets library name (telemetry) |
| `.WithDebugLoggingCallback()` | Enables `Debug.Write` traces |
| `.WithLogging()` | Enables custom logging callback |
| `.WithTelemetry(callback)` | Sets telemetry delegate |

### Confidential-Specific Modifiers

- `.WithCertificate(X509Certificate2)` and `.WithClientSecret(string)` are **mutually exclusive** — providing both throws an exception.
- Full list in `ConfidentialClientApplicationBuilder` class documentation.

## Related Pages

- [[msal]] – MSAL overview
- [[msal-overview]] – MSAL library overview source
- [[service-principals]] – registration provides the IDs needed here
- [[microsoft-identity-platform]] – the platform being targeted
