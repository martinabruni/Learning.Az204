---
title: "Secure APIs by Using Certificates"
type: source
tags: [api-management, security, certificates, tls, mutual-auth, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Secure APIs by Using Certificates

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf

## Overview

Certificates enable **TLS mutual authentication** between the client and the [[apim-gateway|API Management gateway]]. Certificate authorization is handled through inbound policies.

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf
> "Certificates can be used to provide Transport Layer Security (TLS) mutual authentication between the client and the API gateway."

## Key Claims

- The gateway can be configured to allow only requests with certificates meeting specific criteria.
- Certificate authorization is implemented in [[apim-policies|inbound processing policies]].
- Multiple certificate properties can be combined in a single policy check.
- The Consumption tier requires **explicitly enabling** client certificates (on the Custom domains page); other tiers do not.
- Self-signed certificates require trusting the source explicitly.

## TLS Client Authentication Properties

The gateway can inspect the following certificate properties:

| Property | Description |
|----------|-------------|
| Certificate Authority (CA) | Only allow certificates signed by a particular CA |
| Thumbprint | Allow certificates containing a specified thumbprint |
| Subject | Only allow certificates with a specified subject |
| Expiration Date | Reject expired certificates |

Properties are not mutually exclusive and can be combined.

## Certificate Verification

Two common ways to verify client certificates:
1. **Check the issuer**: if the CA is trusted, configure trusted CAs in the Azure portal to automate verification.
2. **Trust the source** for self-signed certificates.

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf
> "Client certificates are signed to ensure that they aren't tampered with."

## Certificate Authorization Policies

### Check Thumbprint (single certificate)

```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    context.Request.Certificate.Thumbprint != 'desired-thumbprint')" >
    <return-response>
      <set-status code="403" reason="Invalid client certificate" />
    </return-response>
  </when>
</choose>
```

### Check Thumbprint Against Uploaded Certificates (multiple partners)

Certificates are uploaded via the **Client certificates** page in the Azure portal.

```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    !context.Request.Certificate.Verify() ||
    !context.Deployment.Certificates.Any(c =>
      c.Value.Thumbprint == context.Request.Certificate.Thumbprint))" >
    <return-response>
      <set-status code="403" reason="Invalid client certificate" />
    </return-response>
  </when>
</choose>
```

### Check Issuer and Subject

```xml
<choose>
  <when condition="@(context.Request.Certificate == null ||
    context.Request.Certificate.Issuer != 'trusted-issuer' ||
    context.Request.Certificate.SubjectName.Name != 'expected-subject-name')" >
    <return-response>
      <set-status code="403" reason="Invalid client certificate" />
    </return-response>
  </when>
</choose>
```

## Consumption Tier Note

- The Consumption tier conforms to serverless design principles.
- Suitable for APIs built on serverless technologies such as **Azure Functions**.
- Requires explicit enablement of client certificate requests on the **Custom domains** page.

## Data Points

- `context.Request.Certificate` exposes the client certificate in policy expressions.
- `context.Deployment.Certificates` holds the store of certificates uploaded to API Management.
- Thumbprint is a hash calculated from other certificate properties, ensuring tamper-evidence.
- Response code for failed certificate auth: `403`.

## Related Pages

- [[apim-certificates]] – concept page for certificate-based auth
- [[apim-gateway]] – gateway that enforces certificate policies
- [[apim-policies]] – inbound policies used for certificate checks
- [[azure-api-management]] – parent service entity
- [[apim-subscriptions]] – alternative security mechanism (subscription keys)
- [[tls-mutual-auth]] – TLS mutual authentication concept
