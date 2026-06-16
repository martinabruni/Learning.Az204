---
title: "Azure Monitor"
type: entity
tags: [azure-monitor, monitoring, observability, az204]
sources: [application-insights-overview.md, app-instrumentation.md]
created: 2026-06-16
updated: 2026-06-16
---

# Azure Monitor

## What It Is

Azure Monitor is the unified monitoring platform in Microsoft Azure. It collects, analyzes, and acts on telemetry data from cloud and on-premises environments.

## Relationship to Application Insights

[[application-insights]] is an **extension of Azure Monitor** that provides APM (Application Performance Monitoring) capabilities. Application Insights sends telemetry to Azure Monitor for analysis and presentation.

## Key Integration Points

- Application Insights SDKs and autoinstrumentation both send telemetry to Azure Monitor.
- [[azure-monitor]] OpenTelemetry Distros are one of the two manual instrumentation options available for Application Insights.
- Azure Monitor receives host diagnostics from Docker and Azure environments monitored by Application Insights.

## Related Pages

- [[application-insights]] — APM extension of Azure Monitor
- [[application-insights-overview]] — source
- [[app-instrumentation]] — instrumentation source
- [[opentelemetry]] — related standard
