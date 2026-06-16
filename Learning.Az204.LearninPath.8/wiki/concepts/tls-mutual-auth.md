---
title: "TLS Mutual Authentication"
type: concept
tags: [tls, mutual-auth, certificates, security, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_7-secure-access-api-certificates.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# TLS Mutual Authentication

## Definition

TLS mutual authentication (mTLS) is an extension of standard TLS where **both parties** — client and server — present and verify certificates. In standard TLS, only the server is authenticated; in mTLS, the client is also authenticated.

## How It Works in API Management

1. The client sends a request to the [[apim-gateway|API Management gateway]] with a client certificate.
2. The gateway inspects the certificate's properties (thumbprint, CA, subject, expiration).
3. If the certificate meets the configured policy criteria, the request proceeds; otherwise, a `403 Invalid client certificate` response is returned.

## Certificate Properties Checked

- **Thumbprint**: hash derived from certificate properties; ensures tamper evidence.
- **Certificate Authority (CA)**: validates the certificate was issued by a trusted authority.
- **Subject**: validates the identity asserted by the certificate.
- **Expiration Date**: ensures the certificate is still valid.

## Verification Approaches

| Method | Use Case |
|--------|----------|
| CA-signed | Certificates from a trusted CA; configure trusted CAs in Azure portal |
| Self-signed | Certificates from known partners; upload to API Management's certificate store |

## Security Guarantees

- Client certificates are **signed**, preventing tampering after issuance.
- Thumbprint calculation makes alteration detectable.
- Multiple properties can be combined for defense-in-depth.

## Consumption Tier Note

In the Consumption tier of [[azure-api-management]], client certificate validation must be explicitly enabled on the Custom domains page before it can be used.

## Related Pages

- [[apim-certificates]] – implementation details in APIM
- [[apim-policies]] – inbound policies that implement mTLS checks
- [[apim-gateway]] – where mTLS enforcement occurs
- [[azure-api-management]] – the service
- [[secure-access-api-certificates]] – source page
