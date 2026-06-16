---
title: "Wiki Activity Log – AZ-204 Learning Path 11"
type: synthesis
tags: [log, az204, monitoring]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log — AZ-204 Learning Path 11

Append-only chronological log of all wiki operations.

---

## [2026-06-16] ingest | Explore Application Insights
- Added: sources/application-insights-overview.md, entities/application-insights.md, entities/azure-monitor.md, concepts/apm.md
- Updated: index.md, log.md
- Key takeaways: Application Insights is an Azure Monitor extension providing APM via proactive and reactive telemetry. Key features include Live Metrics, Availability tests, Smart Detection, Application Map, and Distributed Tracing. Monitors requests, dependencies, exceptions, page views, AJAX calls, user sessions, performance counters, and custom events. Free basic plan; no charge until substantial usage.

## [2026-06-16] ingest | Discover Log-Based Metrics
- Added: sources/logs-based-metrics.md, concepts/log-based-metrics.md
- Updated: entities/application-insights.md, index.md, log.md
- Key takeaways: Application Insights has two metric types — log-based (translated to Kusto queries from events; more dimensions; better for diagnostics) and standard/preaggregated (stored as time series; faster queries; better for dashboards and real-time alerts). Preaggregation introduced in Application Insights 2.7 SDK for .NET. Ingestion sampling never affects preaggregated metric accuracy.

## [2026-06-16] ingest | Instrument an App for Monitoring
- Added: sources/app-instrumentation.md, entities/opentelemetry.md, concepts/autoinstrumentation.md
- Updated: entities/application-insights.md, index.md, log.md
- Key takeaways: Two instrumentation approaches — autoinstrumentation (no code changes, configuration only, less configurable) and manual instrumentation (Application Insights SDKs or Azure Monitor OpenTelemetry Distros). Microsoft is a Platinum CNCF Member and helped create OpenTelemetry from OpenCensus + OpenTracing. OpenTelemetry terms are progressively replacing Application Insights legacy terms.

## [2026-06-16] ingest | Select an Availability Test
- Added: sources/availability-tests.md, concepts/availability-tests.md
- Updated: entities/application-insights.md, index.md, log.md
- Key takeaways: Three availability test types — Standard test (recommended, includes TLS/SSL check), Custom TrackAvailability (most flexible, uses TrackAvailability() method), and URL ping test (classic, DEPRECATED, retiring September 30 2026). Up to 100 tests per resource. Tests require no app changes and work for any public HTTP/HTTPS endpoint or REST API.

## [2026-06-16] ingest | Troubleshoot App Performance by Using Application Map
- Added: sources/application-map-source.md, concepts/application-map.md, concepts/distributed-tracing.md
- Updated: entities/application-insights.md, index.md, log.md
- Key takeaways: Application Map visually shows distributed app topology with health KPIs per component. Discovers components by following HTTP dependency calls. Components are distinct from observed external dependencies (SQL, Event Hubs). Uses cloud role name property for identification; can be overridden. Supports progressive discovery and drill-down into Application Insights events and Azure diagnostics (e.g., SQL Database Advisor).
