---
title: "Create Advanced Policies"
type: source
tags: [api-management, policies, advanced, control-flow, retry, event-hubs, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-api-management_5-create-advanced-policies.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Create Advanced Policies

> [!source] learn.microsoft.com_en-us_training_modules_explore-api-management_5-create-advanced-policies.pdf

## Overview

Reference for six advanced [[apim-policies|API Management policies]] that handle control flow, concurrency, logging, mocking, and retry logic.

## Key Claims

- Advanced policies give fine-grained control over API pipeline execution.
- Policies can be combined and nested.
- When requests exceed concurrency limits, the gateway returns `429 Too Many Requests` immediately.
- The `mock-response` policy prefers examples over schemas when generating responses.

## Policy Reference

### 1. Control Flow (`<choose>`)

Conditionally applies policy statements based on Boolean expressions — similar to `if-then-else` or `switch`.

```xml
<choose>
  <when condition="Boolean expression | Boolean constant">
    <!-- policies applied if condition is true -->
  </when>
  <otherwise>
    <!-- policies applied if no <when> condition is true -->
  </otherwise>
</choose>
```

- Must contain at least one `<when/>` element.
- `<otherwise/>` is optional.
- Conditions evaluated in order of appearance.

### 2. Forward Request (`<forward-request>`)

Forwards the incoming request to the backend service specified in the request context.

```xml
<forward-request timeout="time in seconds" follow-redirects="true | false"/>
```

- Removing this policy prevents forwarding to the backend.
- Outbound policies evaluate immediately after inbound policies complete successfully.

### 3. Limit Concurrency (`<limit-concurrency>`)

Prevents enclosed policies from executing by more than the specified number of requests at any time.

```xml
<limit-concurrency key="expression" max-count="number">
  <!-- nested policy statements -->
</limit-concurrency>
```

- Exceeding `max-count` returns `429 Too Many Requests` immediately.

### 4. Log to Event Hubs (`<log-to-eventhub>`)

Sends messages to an Azure Event Hub defined by a Logger entity; used for online or offline analysis.

```xml
<log-to-eventhub logger-id="id of the logger entity"
                 partition-id="index of the partition"
                 partition-key="value used for partition assignment">
  Expression returning a string to be logged
</log-to-eventhub>
```

### 5. Mock Response (`<mock-response>`)

Aborts pipeline execution and returns a mocked response to the caller.

```xml
<mock-response status-code="code" content-type="media type"/>
```

- Priority order for response generation: **examples** > **schemas** > **no-content response**.
- Useful for development and testing before backend is ready.

### 6. Retry (`<retry>`)

Retries child policies until the condition becomes `false` or retry count is exhausted.

```xml
<retry
  condition="boolean expression or literal"
  count="number of retry attempts"
  interval="retry interval in seconds"
  max-interval="maximum retry interval in seconds"
  delta="retry interval delta in seconds"
  first-fast-retry="boolean expression or literal">
  <!-- One or more child policies -->
</retry>
```

### 7. Return Response (`<return-response>`)

Aborts pipeline execution and returns a default or custom response.

```xml
<return-response response-variable-name="existing context variable">
  <set-header/>
  <set-body/>
  <set-status/>
</return-response>
```

- Default response: `200 OK` with no body.
- When both `response-variable-name` and inner policy statements are provided, statements modify the context variable first.

## Data Points

- `limit-concurrency` uses a `key` expression to scope the concurrency limit.
- `log-to-eventhub` requires a Logger entity configured in API Management.
- `retry` supports exponential backoff via `delta` and `max-interval` parameters.
- `mock-response` always tries to return highest-fidelity responses.

## Related Pages

- [[apim-policies]] – general policy concept
- [[apim-advanced-policies]] – concept page for advanced policies
- [[azure-api-management]] – parent service
- [[azure-event-hubs]] – Event Hubs entity (used with log-to-eventhub)
- [[api-management-policies]] – basic policy configuration source
