---
title: "Application Insights"
type: entity
tags: [application-insights, azure-monitor, apm, monitoring, az204]
sources: [application-insights-overview.md, logs-based-metrics.md, app-instrumentation.md, availability-tests.md, application-map-source.md]
created: 2026-06-16
updated: 2026-06-16
---

# Application Insights

## What It Is

Application Insights is an extension of [[azure-monitor]] that provides **Application Performance Monitoring (APM)** features. It is a fully managed, Azure-hosted service for collecting, storing, and visualizing application telemetry.

## Core Capabilities

- **Live Metrics** — real-time activity observation with no host environment impact
- **Availability tests** — synthetic probing of external endpoints from global locations (see [[availability-tests]])
- **Smart Detection** — automatic failure and anomaly detection via proactive telemetry analysis
- **Application Map** — visual topology of distributed app components with health indicators (see [[application-map]])
- **Distributed Tracing** — end-to-end flow visualization for a given execution or transaction (see [[distributed-tracing]])
- **Usage analytics** — feature popularity and user interaction data
- **GitHub / Azure DevOps integration** — work item creation in context of telemetry data

## Metrics System

Two coexisting metric types:
- **Log-based metrics** — translated to Kusto queries from stored events; more dimensions; better for ad-hoc diagnostics
- **Standard metrics (preaggregated)** — stored as time series; better query performance; preferred for dashboards and real-time alerts

See [[log-based-metrics]].

## Instrumentation Methods

| Method | How |
|--------|-----|
| Autoinstrumentation | Configuration-only; no code changes |
| Application Insights SDK | Manual; install language-specific package |
| Azure Monitor OpenTelemetry Distros | Manual; follows [[opentelemetry]] standard |

See [[autoinstrumentation]].

## Pricing

- Free to sign up.
- No charge on basic pricing plan until substantial usage is reached.

## Capacity

- Up to **100 availability tests** per Application Insights resource.

## Key Identifiers

- Telemetry is directed to an Application Insights resource using a **unique instrumentation token/key**.
- The **cloud role name** property identifies components on the Application Map.

## Related Pages

- [[azure-monitor]] — parent service
- [[application-insights-overview]] — overview source
- [[logs-based-metrics]] — metrics source
- [[app-instrumentation]] — instrumentation source
- [[availability-tests]] — availability source
- [[application-map-source]] — Application Map source
- [[log-based-metrics]] — concept
- [[application-map]] — concept
- [[distributed-tracing]] — concept
- [[availability-tests]] — concept
- [[opentelemetry]] — concept
- [[autoinstrumentation]] — concept
