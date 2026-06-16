---
title: "API Management Certificate Authentication"
type: concept
tags: [api-management, certificates, tls, mutual-auth, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# API Management Certificate Authentication

## Definition

Client certificates provide **TLS mutual authentication** in [[azure-api-management]], allowing the [[apim-gateway|gateway]] to verify the identity of clients. Authorization is implemented through **inbound [[apim-policies|policies]]**.

## Certificate Properties for Inspection

| Property | Description |
|----------|-------------|
| Certificate Authority (CA) | Only allow certificates signed by a specific CA |
| Thumbprint | Allow certificates with a specific thumbprint |
| Subject | Only allow certificates with a specified subject name |
| Expiration Date | Reject expired certificates |

Properties can be combined in a single policy check.

## Certificate Verification Methods

1. **CA-signed certificates**: configure trusted CAs in the Azure portal; verification is automated.
2. **Self-signed certificates**: trust must be explicitly configured; certificates uploaded via the Client certificates page.

## Policy Implementation Patterns

### Check single thumbprint
```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    context.Request.Certificate.Thumbprint != 'desired-thumbprint')" >
    <return-response><set-status code="403" reason="Invalid client certificate" /></return-response>
  </when>
</choose>
```

### Check thumbprint against uploaded store (multi-partner)
```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    !context.Request.Certificate.Verify() ||
    !context.Deployment.Certificates.Any(c =>
      c.Value.Thumbprint == context.Request.Certificate.Thumbprint))" >
    <return-response><set-status code="403" reason="Invalid client certificate" /></return-response>
  </when>
</choose>
```

### Check issuer and subject
```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    context.Request.Certificate.Issuer != 'trusted-issuer' ||
    context.Request.Certificate.SubjectName.Name != 'expected-subject-name')" >
    <return-response><set-status code="403" reason="Invalid client certificate" /></return-response>
  </when>
</choose>
```

## Consumption Tier Special Requirement

- Client certificates must be **explicitly enabled** on the **Custom domains** page.
- Other tiers do not require this explicit step.
- The Consumption tier is designed for serverless workloads (e.g., [[azure-functions]]).

## Key Context Variables

| Variable | Usage |
|----------|-------|
| `context.Request.Certificate` | The client certificate from the request |
| `context.Request.Certificate.Thumbprint` | Thumbprint for comparison |
| `context.Request.Certificate.Issuer` | Certificate issuer |
| `context.Request.Certificate.SubjectName.Name` | Certificate subject |
| `context.Request.Certificate.Verify()` | Validates certificate chain |
| `context.Deployment.Certificates` | Store of uploaded partner certificates |

## Related Pages

- [[tls-mutual-auth]] – TLS mutual authentication concept
- [[apim-policies]] – inbound policies for certificate enforcement
- [[apim-gateway]] – where certificate checks are applied
- [[azure-api-management]] – parent service
- [[apim-subscriptions]] – alternative security mechanism
- [[secure-access-api-certificates]] – source page
