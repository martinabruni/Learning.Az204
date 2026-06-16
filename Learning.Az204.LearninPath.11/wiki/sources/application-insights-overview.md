---
title: "Explore Application Insights"
type: source
tags: [application-insights, azure-monitor, apm, telemetry, monitoring, az204]
sources: [learn.microsoft.com_en-us_training_modules_monitor-app-performance_2-application-insights-overview.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Application Insights

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_2-application-insights-overview.pdf

## Overview

[[application-insights]] is an extension of [[azure-monitor]] and provides Application Performance Monitoring (APM) features. It is used to monitor applications from development, through test, and into production.

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_2-application-insights-overview.pdf
> "Application Insights is an extension of Azure Monitor and provides Application Performance Monitoring (APM) features."

Two primary use modes:
- **Proactively** understand how an application is performing.
- **Reactively** review application execution data to determine the cause of an incident.

In addition to metrics and telemetry, Application Insights can collect and store **application trace logging data**. Log traces are associated with other telemetry for a detailed activity view.

## Key Claims

- Application Insights collects metrics, telemetry, and trace logs.
- Adding trace logging to existing apps only requires providing a destination; the logging framework rarely needs to change.
- Application Insights is free to sign up; no charge until substantial usage on the basic pricing plan.

## Feature Overview

| Feature | Description |
|---------|-------------|
| Live Metrics | Observe deployed app activity in real time with no effect on the host environment |
| Availability | Synthetic Transaction Monitoring — probe external endpoints to test availability and responsiveness over time |
| GitHub / Azure DevOps integration | Create work items in context of Application Insights data |
| Usage | Understand which features are popular and how users interact with the application |
| Smart Detection | Automatic failure and anomaly detection through proactive telemetry analysis |
| Application Map | High-level top-down view of application architecture with component health and responsiveness |
| Distributed Tracing | Search and visualize end-to-end flow of a given execution or transaction |

## What Application Insights Monitors

- **Request rates, response times, failure rates** — popular pages, peak times, user geography
- **Dependency rates, response times, failure rates** — whether external services are slowing the app
- **Exceptions** — aggregated stats or specific instances with stack traces; both server and browser exceptions
- **Page views and load performance** — from users' browsers
- **AJAX calls** — rates, response times, failure rates
- **User and session counts**
- **Performance counters** — CPU, memory, network usage from Windows/Linux servers
- **Host diagnostics** from Docker or Azure
- **Diagnostic trace logs** — correlate trace events with requests
- **Custom events and metrics** — business events written in client or server code

## Getting Started

Four entry points:

1. **At run time** — instrument the web app on the server; no code changes required; ideal for already-deployed apps.
2. **At development time** — add Application Insights to your code; customize telemetry and send more data.
3. **Instrument web pages** — page view, AJAX, client-side telemetry.
4. **Analyze mobile app usage** — integrate with Visual Studio App Center.
5. **Availability tests** — ping the website regularly from Azure servers.

## Related Pages

- [[application-insights]] — entity page
- [[azure-monitor]] — parent service
- [[apm]] — concept
- [[distributed-tracing]] — concept
- [[availability-tests]] — concept
- [[application-map]] — concept
- [[logs-based-metrics]] — source, next unit
