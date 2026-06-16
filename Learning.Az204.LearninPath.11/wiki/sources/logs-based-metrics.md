---
title: "Discover Log-Based Metrics"
type: source
tags: [application-insights, metrics, logs, kusto, preaggregated, az204]
sources: [learn.microsoft.com_en-us_training_modules_monitor-app-performance_3-logs-based-metrics.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Discover Log-Based Metrics

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_3-logs-based-metrics.pdf

## Overview

[[application-insights]] offers two kinds of metrics for analyzing app health, building dashboards, and configuring alerts:

| Type | Storage | Best for |
|------|---------|----------|
| **Log-based metrics** | Translated into Kusto queries from stored events | Data analysis and ad-hoc diagnostics (more dimensions) |
| **Standard metrics (preaggregated)** | Stored as preaggregated time series | Dashboarding and real-time alerting (better query performance) |

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_3-logs-based-metrics.pdf
> "Both, log-based and pre-aggregated metrics coexist in Application Insights. To differentiate the two, in the Application Insights UX the pre-aggregated metrics are now called Standard metrics (preview), while the traditional metrics from the events were renamed to Log-based metrics."

## Key Claims

- Standard metrics are preaggregated during collection, giving better query-time performance.
- Log-based metrics have more dimensions, making them superior for data analysis and ad-hoc diagnostics.
- Use the **namespace selector** in Metrics Explorer to switch between log-based and standard metrics.

## Log-Based Metrics

- Developers send events via SDK (manual) or rely on **autoinstrumentation** (automatic).
- The Application Insights backend stores all collected events as logs.
- Application Insights blades in the Azure portal act as analytical/diagnostic tools for visualizing event-based data.
- Benefits: exact request counts per URL, distinct user counts, detailed diagnostic traces including exceptions and dependency calls.
- Drawback: for high-volume telemetry apps, Application Insights applies **sampling and filtering** to reduce stored events, which can lower metric accuracy at query time.

## Preaggregated Metrics

- Not stored as individual events — stored as **preaggregated time series** with key dimensions only.
- Faster retrieval at query time; requires less compute power.
- Enables **near real-time alerting** on metric dimensions and more responsive dashboards.
- **Application Insights 2.7 SDK or later for .NET** preaggregates metrics during collection.
- Accuracy is **not affected by sampling or filtering** because preaggregation happens before ingestion sampling.
- `GetMetric` API for custom metrics → less data ingestion, lower cost.
- For older SDKs without preaggregation: the backend still populates preaggregated metrics by aggregating events at the collection endpoint.

## Data Point

- Application Insights 2.7 SDK (.NET) introduced client-side preaggregation.
- Ingestion sampling never impacts the accuracy of preaggregated metrics, regardless of SDK version.

## Related Pages

- [[application-insights]] — entity page
- [[azure-monitor]] — parent service
- [[log-based-metrics]] — concept page
- [[application-insights-overview]] — previous unit
- [[app-instrumentation]] — next unit
