---
title: "Distributed Tracing"
type: concept
tags: [distributed-tracing, application-insights, opentelemetry, microservices, az204]
sources: [application-insights-overview.md, application-map-source.md, app-instrumentation.md]
created: 2026-06-16
updated: 2026-06-16
---

# Distributed Tracing

## Definition

Distributed tracing is the practice of tracking a single request or transaction as it flows across multiple services, components, or processes in a distributed system. It provides end-to-end visibility into execution flows.

## In Application Insights

[[application-insights]] provides distributed tracing as a built-in feature: it lets you **search and visualize an end-to-end flow** of a given execution or transaction.

## OpenTelemetry Alignment

In [[opentelemetry]] terminology, distributed tracing concepts map as follows:

| Application Insights | OpenTelemetry |
|---------------------|---------------|
| Requests | Server Spans |
| Dependencies | Other Span Types (Client, Internal, etc.) |
| Operation ID | Trace ID |
| ID or Operation Parent ID | Span ID |
| Traces | Logs |

## Relationship to Application Map

[[application-map]] visualizes the topology and health of distributed application components. Clicking a component in the Application Map leads to distributed trace details and performance/failure triage for that component.

## Key Identifiers

- **Trace ID** (Operation ID) — identifies the overall distributed transaction.
- **Span ID** (Operation Parent ID) — identifies a single unit of work within the trace.

## Related Pages

- [[application-insights]] — entity providing distributed tracing
- [[opentelemetry]] — standard that aligns with Application Insights tracing
- [[application-map]] — visual topology relying on distributed tracing data
- [[application-insights-overview]] — source
- [[app-instrumentation]] — source
