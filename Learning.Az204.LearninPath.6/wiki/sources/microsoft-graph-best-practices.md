---
title: "Apply Best Practices to Microsoft Graph"
type: source
tags: [microsoft-graph, best-practices, pagination, authentication, az204]
sources: [learn.microsoft.com_en-us_training_modules_microsoft-graph_5-microsoft-graph-best-practices.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Apply Best Practices to Microsoft Graph

> [!source] learn.microsoft.com_en-us_training_modules_microsoft-graph_5-microsoft-graph-best-practices.pdf

## Overview

Best practices for maximizing reliability and correctness when using [[microsoft-graph]].

## Key Claims

### Authentication

- Acquire an **OAuth 2.0 access token** and present it to Microsoft Graph via:
  - HTTP `Authorization` header as a **Bearer token**.
  - Graph client constructor (when using an SDK).
- Use **[[msal|MSAL]]** to acquire the access token.

### Consent and Authorization Best Practices

- **Use least privilege** — request only permissions needed, and only when needed.
- **Use the correct permission type**:
  - Interactive app with signed-in user → use **delegated permissions**.
  - Background service/daemon without signed-in user → use **application permissions**.
  - Warning: application permissions in interactive scenarios create compliance and security risks.
- **Consider end user and admin experience**: understand who is consenting; understand static vs. dynamic vs. incremental consent.
- **Consider multi-tenant applications**: tenant admins may restrict user consent or set custom authorization policies (expect HTTP 403 errors when acting on behalf of users in restricted tenants).

### Handle Responses Effectively

- **Pagination**: Microsoft Graph returns collections in **multiple pages** (server-side page size limits). Always handle `@odata.nextLink` and read all pages until the final page (no `@odata.nextLink`).
- **Evolvable enumerations**: Microsoft Graph uses evolvable enums to add new members without breaking changes. By default, GET returns only known members. Opt in to receive unknown members using HTTP `Prefer` request header.

### Storing Data Locally

- Prefer making **real-time calls** to Microsoft Graph rather than caching.
- Only cache/store data necessary for a specific scenario.
- Comply with terms of use, privacy policy, and Microsoft APIs Terms of Use.
- Implement proper **retention and deletion policies** if storing data locally.

## Related Pages

- [[microsoft-graph]] – entity page
- [[microsoft-graph-rest-api]] – REST querying
- [[microsoft-graph-sdk]] – SDK-based access
- [[permissions-and-consent]] – relates to consent best practices
- [[msal]] – used for token acquisition
