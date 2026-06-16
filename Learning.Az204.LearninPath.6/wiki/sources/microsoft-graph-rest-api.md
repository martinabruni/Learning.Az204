---
title: "Query Microsoft Graph by Using REST"
type: source
tags: [microsoft-graph, rest-api, odata, http, az204]
sources: [learn.microsoft.com_en-us_training_modules_microsoft-graph_3-microsoft-graph-api.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Query Microsoft Graph by Using REST

> [!source] learn.microsoft.com_en-us_training_modules_microsoft-graph_3-microsoft-graph-api.pdf

## Overview

[[microsoft-graph]] is a RESTful web API. After registering an app and obtaining authentication tokens, you can make requests to the Microsoft Graph API.

## Key Claims

### Request Structure

```
{HTTP method} https://graph.microsoft.com/{version}/{resource}?{query-parameters}
```

Components:
- `{HTTP method}` — the operation to perform.
- `{version}` — API version (`v1.0` or `beta`).
- `{resource}` — the Microsoft Graph resource being addressed.
- `{query-parameters}` — optional OData query options or REST parameters.

### HTTP Methods

| Method | Description |
|--------|-------------|
| GET | Read data from a resource |
| POST | Create a new resource or perform an action |
| PATCH | Update a resource with new values |
| PUT | Replace a resource with a new one |
| DELETE | Remove a resource |

- GET and DELETE: **no request body** required.
- POST, PATCH, PUT: require a **JSON request body**.

### Versions

- **v1.0** — generally available APIs; use in **production apps**.
- **beta** — preview APIs; may include breaking changes; use **only in development**.

### Resources and Relationships

- Resources include: `me`, `user`, `group`, `drive`, `site`.
- Top-level resources support relationships: `me/messages`, `me/drive`.
- Resources can be accessed via methods: `me/sendMail`.
- Most resources, methods, and enumerations are in the `microsoft.graph` OData namespace.

### Response Components

- **Status code** — HTTP status indicating success or failure.
- **Response message** — requested data or operation result (may be empty).
- **`@odata.nextLink`** — URL for the next page when results are paginated.

### Query Parameters (OData)

- Use `$filter` to filter results: `?filter=emailAddress eq 'jon@contoso.com'`
- Use `$select` to request specific properties.
- Use `$orderBy` to sort results.

### Related Tools

- Graph Explorer (browser-based testing)
- Postman

## Related Pages

- [[microsoft-graph]] – entity page
- [[microsoft-graph-sdk]] – SDK-based access
- [[microsoft-graph-best-practices]] – best practices
- [[oauth2-and-openid-connect]] – used to obtain access tokens for requests
