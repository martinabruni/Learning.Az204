---
title: "Wiki Index – AZ-204 Learning Path 11: Monitor App Performance"
type: synthesis
tags: [index, az204, application-insights, azure-monitor, monitoring]
sources: [application-insights-overview.md, logs-based-metrics.md, app-instrumentation.md, availability-tests.md, application-map-source.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 11: Monitor App Performance

This wiki is built from the 5 PDFs in `raw/`, covering the Microsoft Learn module "Monitor app performance" focused on Azure Application Insights.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[application-insights]] | Azure Monitor extension providing APM features: telemetry, metrics, traces, availability testing |
| [[azure-monitor]] | Unified Azure monitoring platform; parent service of Application Insights |
| [[opentelemetry]] | CNCF open-source observability standard; Microsoft is a Platinum Member; terms replacing legacy Application Insights terms |

---

## Concepts

| Page | Summary |
|------|---------|
| [[apm]] | Application Performance Monitoring discipline: proactive and reactive app health monitoring |
| [[log-based-metrics]] | Two metric types in Application Insights — log-based (more dimensions, ad-hoc) vs. standard preaggregated (faster, dashboards) |
| [[autoinstrumentation]] | Codeless telemetry collection via configuration; no code changes; less configurable than SDK-based approach |
| [[availability-tests]] | Recurring synthetic probes (up to 100 per resource) testing HTTP/HTTPS endpoints from global locations |
| [[application-map]] | Visual topology of distributed app components with health KPIs; discovers components via HTTP dependency calls |
| [[distributed-tracing]] | End-to-end flow tracking across distributed services; aligns with OpenTelemetry Trace ID / Span ID model |

---

## Sources — Module: Monitor App Performance

| Page | PDF |
|------|-----|
| [[application-insights-overview]] | `monitor-app-performance_2-application-insights-overview.pdf` |
| [[logs-based-metrics]] | `monitor-app-performance_3-logs-based-metrics.pdf` |
| [[app-instrumentation]] | `monitor-app-performance_4-app-instrumentation.pdf` |
| [[availability-tests]] | `monitor-app-performance_5-availability-tests.pdf` |
| [[application-map-source]] | `monitor-app-performance_6-application-map.pdf` |

---

## Page Counts

- Sources: 5
- Entities: 3
- Concepts: 6
- **Total wiki pages: 14** (plus this index and log.md)
