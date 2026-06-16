---
title: "Application Performance Monitoring (APM)"
type: concept
tags: [apm, monitoring, observability, application-insights, az204]
sources: [application-insights-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Application Performance Monitoring (APM)

## Definition

APM (Application Performance Monitoring) is the discipline of monitoring software applications to detect performance issues, failures, and usage patterns throughout the software lifecycle — from development, through testing, and into production.

## Two Modes of Use

- **Proactive** — understand how an application is performing before issues occur.
- **Reactive** — review execution data after an incident to identify its cause.

## Azure Implementation

[[application-insights]] is Microsoft's APM solution and is an extension of [[azure-monitor]].

## What APM Tools Typically Collect

- Request rates, response times, failure rates
- Dependency rates and latencies
- Exceptions (server and browser)
- Page views and load times
- User and session counts
- Custom business events and metrics
- Infrastructure performance counters (CPU, memory, network)

## Related Pages

- [[application-insights]] — Azure APM service
- [[application-insights-overview]] — source
- [[distributed-tracing]] — related observability concept
