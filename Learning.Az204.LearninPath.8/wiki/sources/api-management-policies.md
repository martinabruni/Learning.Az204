---
title: "Explore API Management Policies"
type: source
tags: [api-management, policies, xml, policy-expressions, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_4-api-management-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore API Management Policies

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_4-api-management-policies.pdf

## Overview

[[apim-policies|Policies]] allow the API publisher to change API behavior through configuration. They are a collection of statements executed sequentially on the request or response, applied inside the [[apim-gateway|gateway]].

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_4-api-management-policies.pdf
> "Policies are a collection of Statements that are executed sequentially on the request or response of an API."

## Key Claims

- Policies can apply changes to both the **inbound request** and **outbound response**.
- Policy expressions can be used as attribute values or text values in any policy (unless the policy specifies otherwise).
- On error, remaining inbound/backend/outbound steps are skipped and the `on-error` section executes.

## Policy Configuration Structure

The policy definition is an XML document divided into four sections:

```xml
<policies>
  <inbound>
    <!-- statements applied to the request -->
  </inbound>
  <backend>
    <!-- statements applied before forwarding to the backend -->
  </backend>
  <outbound>
    <!-- statements applied to the response -->
  </outbound>
  <on-error>
    <!-- statements applied if an error occurs -->
  </on-error>
</policies>
```

Statements execute in order within each section.

## Error Handling

- If an error occurs during inbound/backend/outbound processing, execution jumps to `on-error`.
- Use `context.LastError` to review the error.
- Use the `set-body` policy to inspect and customize the error response.

## Policy Expressions

A policy expression is either:
- A **single C# statement** enclosed in `@(expression)`
- A **multi-statement C# code block** enclosed in `@{expression}` that returns a value

Each expression has access to the implicitly provided `context` variable and an allowed subset of .NET Framework types.

Example using `set-header` to inject user context into requests:

```xml
<policies>
  <inbound>
    <base />
    <set-header name="x-request-context-data" exists-action="override">
      <value>@(context.User.Id)</value>
      <value>@(context.Deployment.Region)</value>
    </set-header>
  </inbound>
</policies>
```

## Policy Scopes and the `<base />` Element

- Policies can be applied at four scopes: **global**, **product**, **API**, **operation**.
- When multiple scopes apply, API Management uses the `<base />` element for deterministic ordering.
- `<base />` inserts the parent scope's policies at that position.

Example with explicit ordering:
```xml
<policies>
  <inbound>
    <cross-domain />  <!-- executes first -->
    <base />          <!-- parent scope policies execute here -->
    <find-and-replace from="xyz" to="abc" />  <!-- executes last -->
  </inbound>
</policies>
```

## Filter Response Content

Policies in the outbound section can filter response payload fields based on the product associated with the request (e.g., strip fields not available in the "Starter" product tier).

## Data Points

- Policy expressions use C# with the `context` variable.
- Error section is triggered on any unhandled exception in the pipeline.
- `context.LastError`, `context.Response`, `context.Product`, `context.User`, `context.Deployment.Region` are all available in expressions.

## Related Pages

- [[apim-policies]] – concept page for policies
- [[apim-advanced-policies]] – advanced policy reference
- [[apim-gateway]] – gateway where policies are applied
- [[azure-api-management]] – parent service
- [[api-management-overview]] – service overview
