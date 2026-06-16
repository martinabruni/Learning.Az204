---
title: "OpenTelemetry"
type: entity
tags: [opentelemetry, cncf, instrumentation, telemetry, az204]
sources: [app-instrumentation.md]
created: 2026-06-16
updated: 2026-06-16
---

# OpenTelemetry

## What It Is

OpenTelemetry is an open-source observability framework and set of APIs, SDKs, and tooling for generating, collecting, and exporting telemetry data (metrics, logs, traces). It lives within the **Cloud Native Computing Foundation (CNCF)**.

## Origin

OpenTelemetry was created by merging two previously popular open-source telemetry projects:
- **OpenCensus** (originated at Google)
- **OpenTracing** (CNCF project)

Microsoft participated in the creation of OpenTelemetry and is a **Platinum Member of the CNCF**.

## Relationship to Application Insights

Microsoft offers **Azure Monitor OpenTelemetry Distros** as one of the two manual instrumentation options for [[application-insights]].

OpenTelemetry terms are replacing legacy Application Insights terms:

| Application Insights (legacy) | OpenTelemetry |
|-------------------------------|---------------|
| Autocollectors | Instrumentation libraries |
| Channel | Exporter |
| Codeless / Agent-based | Autoinstrumentation |
| Traces | Logs |
| Requests | Server Spans |
| Dependencies | Other Span Types (Client, Internal, etc.) |
| Operation ID | Trace ID |
| ID or Operation Parent ID | Span ID |

## Related Pages

- [[application-insights]] — Azure service integrating OpenTelemetry
- [[app-instrumentation]] — source describing integration
- [[autoinstrumentation]] — concept
