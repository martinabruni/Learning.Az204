---
title: "Instrument an App for Monitoring"
type: source
tags: [application-insights, instrumentation, opentelemetry, sdk, autoinstrumentation, az204]
sources: [learn.microsoft.com_en-us_training_modules_monitor-app-performance_4-app-instrumentation.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Instrument an App for Monitoring

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_4-app-instrumentation.pdf

## Overview

"Instrumenting" means enabling an application to capture telemetry. There are two methods:

| Method | Description |
|--------|-------------|
| **Autoinstrumentation** | Enables telemetry collection through configuration; no code changes required; less configurable; not available in all languages |
| **Manual instrumentation** | Coding against the Application Insights or OpenTelemetry API; requires managing SDK version updates |

> [!source] learn.microsoft.com_en-us_training_modules_monitor-app-performance_4-app-instrumentation.pdf
> "Autoinstrumentation enables telemetry collection through configuration without touching the application's code."

## Key Claims

- When autoinstrumentation is available, it is the easiest way to enable [[azure-monitor]] [[application-insights]].
- Manual instrumentation has two options: **Application Insights SDKs** and **Azure Monitor OpenTelemetry Distros**.

## Enabling via Application Insights SDKs

Use the SDK only when:
- Custom events and metrics are required.
- Control over the flow of telemetry is required.
- Autoinstrumentation is not available (language or platform limitations).

SDK installation: install a small instrumentation package in the app, instrument the web app, background components, and JavaScript in web pages. The app does not have to be hosted in Azure. Telemetry is directed to an Application Insights resource using a **unique token**.

SDK version list hosted on GitHub.

## Enable via OpenTelemetry

Microsoft contributed to creating [[opentelemetry]] by merging two previously popular projects:
- **OpenCensus**
- **OpenTracing**

OpenTelemetry lives within the **Cloud Native Computing Foundation (CNCF)**. Microsoft is a **Platinum Member** of the CNCF.

### Terminology Mapping: Application Insights → OpenTelemetry

| Application Insights | OpenTelemetry |
|---------------------|---------------|
| Autocollectors | Instrumentation libraries |
| Channel | Exporter |
| Codeless / Agent-based | Autoinstrumentation |
| Traces | Logs |
| Requests | Server Spans |
| Dependencies | Other Span Types (Client, Internal, etc.) |
| Operation ID | Trace ID |
| ID or Operation Parent ID | Span ID |

## Related Pages

- [[application-insights]] — entity page
- [[opentelemetry]] — concept page
- [[autoinstrumentation]] — concept page
- [[logs-based-metrics]] — previous unit
- [[availability-tests]] — next unit
