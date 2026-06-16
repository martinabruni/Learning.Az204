---
title: "Availability Tests"
type: concept
tags: [availability-tests, synthetic-monitoring, application-insights, az204]
sources: [availability-tests.md]
created: 2026-06-16
updated: 2026-06-16
---

# Availability Tests

## Definition

Availability tests are recurring, automated probes configured in [[application-insights]] that test the availability and responsiveness of a deployed web application or API endpoint. Application Insights sends web requests from **multiple geographic locations** at regular intervals.

Also known as **Synthetic Transaction Monitoring**.

## Key Facts

- No changes required to the application being tested.
- Works for any HTTP or HTTPS endpoint accessible from the public internet.
- Can test REST APIs that a service depends on.
- Up to **100 availability tests** per Application Insights resource.
- Alerts are generated if the application does not respond or responds too slowly.

## Three Test Types

### 1. Standard Test (Recommended)
- Single request per probe cycle.
- Validates endpoint responsiveness and performance.
- Additionally checks:
  - TLS/SSL certificate validity
  - Proactive certificate lifetime
  - HTTP verb support (GET, HEAD, POST)
  - Custom headers
  - Custom request data
- **Recommended** replacement for the deprecated URL ping test.

### 2. Custom TrackAvailability Test
- For custom test scenarios and logic.
- Uses the `TrackAvailability()` SDK method to report results to Application Insights.
- Maximum flexibility.

### 3. URL Ping Test (Classic) — DEPRECATED
- Created through the Azure portal.
- Validates endpoint responsiveness and measures performance.
- Supports custom success criteria, dependent request parsing, and retries.
- **Retirement: September 30, 2026** — migrate to Standard tests before then.

## Migration Note

> URL ping tests will be **retired on September 30, 2026**. Existing tests will be removed from resources. Migrate to Standard tests to continue running single-step availability tests.

## Related Pages

- [[application-insights]] — entity hosting availability tests
- [[availability-tests]] — source page (unit 5)
- [[application-map]] — related troubleshooting tool
- [[apm]] — broader monitoring context
