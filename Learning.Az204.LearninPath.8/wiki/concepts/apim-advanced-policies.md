---
title: "API Management Advanced Policies"
type: concept
tags: [api-management, policies, advanced, control-flow, retry, concurrency, mock, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_5-create-advanced-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# API Management Advanced Policies

## Definition

Advanced [[apim-policies|policies]] provide programmatic control over the API pipeline, enabling conditional logic, concurrency limits, retries, logging, and response mocking.

## Policy Reference

### Control Flow (`<choose>`)

If-then-else logic for conditionally applying policy blocks:

```xml
<choose>
  <when condition="@(context.Response.StatusCode == 200)">
    <!-- ... -->
  </when>
  <otherwise>
    <!-- ... -->
  </otherwise>
</choose>
```

- At least one `<when/>` required.
- `<otherwise/>` optional; applied if all `<when/>` conditions are false.

### Forward Request (`<forward-request>`)

Sends the request to the backend service specified in the API settings.

```xml
<forward-request timeout="30" follow-redirects="false"/>
```

- Removing this policy blocks forwarding to backend.
- Outbound policies run immediately after inbound section completes.

### Limit Concurrency (`<limit-concurrency>`)

Caps parallel executions of enclosed policies.

```xml
<limit-concurrency key="@(context.Subscription.Id)" max-count="5">
  <!-- ... -->
</limit-concurrency>
```

- Requests exceeding `max-count` → `429 Too Many Requests` immediately.
- `key` expression allows per-user or per-subscription concurrency limits.

### Log to Event Hubs (`<log-to-eventhub>`)

Streams request/response context data to [[azure-event-hubs]] for analysis.

```xml
<log-to-eventhub logger-id="logger-id" partition-key="@(context.Request.IpAddress)">
  @(string.Join(",", DateTime.UtcNow, context.Request.Method, context.Request.Url.Path))
</log-to-eventhub>
```

### Mock Response (`<mock-response>`)

Returns a mocked response without calling the backend.

```xml
<mock-response status-code="200" content-type="application/json"/>
```

Response fidelity priority: **examples** > **schemas** > **empty response**.

### Retry (`<retry>`)

Retries child policies using configurable backoff.

```xml
<retry condition="@(context.Response.StatusCode != 200)"
       count="3"
       interval="2"
       max-interval="10"
       delta="1"
       first-fast-retry="true">
  <forward-request/>
</retry>
```

### Return Response (`<return-response>`)

Aborts the pipeline and returns a custom response.

```xml
<return-response>
  <set-status code="200" reason="OK"/>
  <set-header name="Content-Type" exists-action="override"><value>application/json</value></set-header>
  <set-body>{"status":"ok"}</set-body>
</return-response>
```

Default (if no body specified): `200 OK` with no body.

## When to Use Each Policy

| Scenario | Policy |
|----------|--------|
| Feature flags / A/B routing | `<choose>` |
| Throttle per user | `<limit-concurrency>` |
| Audit logging | `<log-to-eventhub>` |
| Stub backend for testing | `<mock-response>` |
| Resilience / transient fault handling | `<retry>` |
| Short-circuit with custom response | `<return-response>` |

## Related Pages

- [[apim-policies]] – basic policy concepts and structure
- [[apim-gateway]] – where policies are applied
- [[azure-api-management]] – parent service
- [[azure-event-hubs]] – log target for `log-to-eventhub`
- [[create-advanced-policies]] – source page
