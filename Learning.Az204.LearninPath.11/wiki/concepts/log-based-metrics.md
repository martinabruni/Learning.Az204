---
title: "Log-Based Metrics vs. Standard (Preaggregated) Metrics"
type: concept
tags: [application-insights, metrics, logs, kusto, preaggregated, az204]
sources: [logs-based-metrics.md]
created: 2026-06-16
updated: 2026-06-16
---

# Log-Based Metrics vs. Standard (Preaggregated) Metrics

## Overview

[[application-insights]] supports two coexisting metric types with distinct characteristics and trade-offs.

## Log-Based Metrics

- Backed by stored event logs.
- Behind the scenes, translated into **Kusto queries** against stored events at query time.
- Support **more dimensions** → superior for data analysis and ad-hoc diagnostics.
- Affected by **sampling and filtering**: when telemetry volume is high and events are reduced, metric accuracy decreases.
- Events can be sent via SDK (manual) or autoinstrumentation (automatic).

## Standard Metrics (Preaggregated)

- Stored as **preaggregated time series** with key dimensions only.
- **Faster query performance** — retrieval requires less compute.
- Not affected by sampling: preaggregation happens **before ingestion sampling** at the collection endpoint.
- Better for **near real-time alerting** on metric dimensions.
- More **responsive dashboards**.
- Introduced in **Application Insights 2.7 SDK (.NET)**.
- Custom metrics via `GetMetric` → lower data ingestion cost.
- Older SDKs without preaggregation: the backend still creates preaggregated metrics from events received at the collection endpoint.

## Naming in the UI

| UI Label | Type |
|----------|------|
| Standard metrics (preview) | Preaggregated metrics |
| Log-based metrics | Traditional event-derived metrics |

Use the **namespace selector** in Metrics Explorer to switch between them.

## When to Use Each

| Scenario | Recommended Type |
|----------|-----------------|
| Dashboard visualizations | Standard metrics |
| Real-time alerting | Standard metrics |
| Ad-hoc diagnostics | Log-based metrics |
| Detailed data analysis | Log-based metrics |
| Counting distinct users per URL | Log-based metrics |

## Related Pages

- [[application-insights]] — entity page
- [[logs-based-metrics]] — source page
- [[apm]] — broader monitoring context
