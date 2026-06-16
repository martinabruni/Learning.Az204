---
title: "API Management Policies"
type: concept
tags: [api-management, policies, xml, policy-expressions, inbound, outbound, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_4-api-management-policies.pdf,
          learn.microsoft.com_en-us_training_modules_explore-api-management_5-create-advanced-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# API Management Policies

## Definition

Policies are a collection of XML statements executed **sequentially** on the request or response of an API, inside the [[apim-gateway|gateway]]. They allow API publishers to change API behavior through configuration without modifying backend code.

## Policy Document Structure

```xml
<policies>
  <inbound>     <!-- applied to the request before backend -->  </inbound>
  <backend>     <!-- applied before forwarding to backend -->   </backend>
  <outbound>    <!-- applied to the response -->                </outbound>
  <on-error>    <!-- applied if an error occurs -->             </on-error>
</policies>
```

## Policy Scopes

Policies can be applied at four scopes (broadest to narrowest):

| Scope | Applies To |
|-------|-----------|
| Global | All APIs in the APIM instance |
| Product | All APIs in a product |
| API | A specific API |
| Operation | A specific API operation |

The `<base />` element controls where parent-scope policies are inserted within the current scope's policy document.

## Policy Expressions

Expressions provide dynamic behavior using C#:

- Single statement: `@(expression)`
- Multi-statement block: `@{expression}` — must return a value

Available context object properties include:
- `context.User.Id`, `context.User.*`
- `context.Deployment.Region`
- `context.Request.Certificate`
- `context.Response.StatusCode`, `context.Response.Body`
- `context.Product.Name`
- `context.LastError`

## Error Handling

- On error, remaining inbound/backend/outbound steps are skipped.
- Execution jumps to `<on-error>`.
- Use `context.LastError` to inspect; use `set-body` to customize the error response.

## Common Policy Statements

| Policy | Purpose |
|--------|---------|
| `set-header` | Add/modify/remove request or response headers |
| `find-and-replace` | String substitution in body or headers |
| `cross-domain` | Enable cross-domain calls |
| `choose` / `when` / `otherwise` | Conditional control flow |
| `set-body` | Modify the request or response body |
| `forward-request` | Forward request to backend |
| `limit-concurrency` | Cap concurrent requests |
| `log-to-eventhub` | Stream log data to Azure Event Hubs |
| `mock-response` | Return a mocked response |
| `retry` | Retry child policies on failure |
| `return-response` | Abort pipeline and return a custom response |

## Related Pages

- [[apim-advanced-policies]] – advanced policy reference
- [[apim-gateway]] – where policies are applied
- [[azure-api-management]] – parent service
- [[api-management-policies]] – source page (basic policy config)
- [[create-advanced-policies]] – source page (advanced policies)
