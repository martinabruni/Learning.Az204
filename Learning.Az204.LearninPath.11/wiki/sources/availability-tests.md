---
title: "Select an Availability Test"
type: source
tags: [application-insights, availability, monitoring, synthetic-monitoring, az204]
sources: [learn.microsoft.com_en-us_training_modules_monitor-app-performance_5-availability-tests.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Select an Availability Test

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_5-availability-tests.pdf

## Overview

After deploying a web app or website, you can set up recurring tests in [[application-insights]] to monitor availability and responsiveness. Application Insights sends web requests from **points around the world** at regular intervals and alerts you if the application isn't responding or responds too slowly.

## Key Claims

- Availability tests do **not require changes** to the website being tested.
- Works for any **HTTP or HTTPS endpoint** accessible from the public internet.
- Can also test the availability of a **REST API** that a service depends on.
- **Up to 100 availability tests** per Application Insights resource.

## Data Point

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_5-availability-tests.pdf
> "URL ping tests: On September 30, 2026, URL ping tests in Application Insights will be retired. Existing URL ping tests will be removed from your resources."

## Three Types of Availability Tests

### 1. Standard Test
- Checks availability by sending a single request (similar to the deprecated URL ping test).
- In addition to endpoint responsiveness and performance, also validates:
  - TLS/SSL certificate validity
  - Proactive lifetime check
  - HTTP request verb (GET, HEAD, POST)
  - Custom headers
  - Custom data associated with HTTP request
- **Recommended replacement** for URL ping tests after September 30, 2026.

### 2. Custom TrackAvailability Test
- For custom applications running availability tests.
- Uses the `TrackAvailability()` method to send results to Application Insights.
- Most flexible option.

### 3. URL Ping Test (Classic) — **DEPRECATED**
- Created through the Azure portal.
- Validates endpoint responsiveness and measures performance.
- Supports custom success criteria, parsing dependent requests, and retries.
- **Retirement date: September 30, 2026** — migrate to Standard tests before then.

## Related Pages

- [[application-insights]] — entity page
- [[availability-tests]] — concept page
- [[app-instrumentation]] — previous unit
- [[application-map-source]] — next unit
