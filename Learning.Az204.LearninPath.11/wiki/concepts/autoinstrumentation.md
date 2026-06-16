---
title: "Autoinstrumentation"
type: concept
tags: [autoinstrumentation, instrumentation, application-insights, opentelemetry, az204]
sources: [app-instrumentation.md]
created: 2026-06-16
updated: 2026-06-16
---

# Autoinstrumentation

## Definition

Autoinstrumentation (also called "codeless" or "agent-based" instrumentation) enables telemetry collection through **configuration only**, without modifying the application's source code.

## Characteristics

- **Convenient** — no code changes required.
- **Less configurable** than manual instrumentation.
- **Not available in all languages and platforms** — check the autoinstrumentation supported environments and languages documentation.
- When available, it is the **easiest way** to enable Azure Monitor Application Insights.

## Comparison with Manual Instrumentation

| Aspect | Autoinstrumentation | Manual (SDK) |
|--------|---------------------|--------------|
| Code changes | None | Required |
| Configurability | Limited | Full control |
| Language support | Limited | Broader |
| Custom events/metrics | Not supported | Supported |
| Dependency management | Managed by platform | Developer-managed |

## Manual Instrumentation Options

When autoinstrumentation is not sufficient or available:
1. **Application Insights SDKs** — language-specific packages; use when custom events/metrics or telemetry flow control are needed.
2. **Azure Monitor OpenTelemetry Distros** — follows [[opentelemetry]] standard; preferred for new projects targeting standards compliance.

## OpenTelemetry Term

In OpenTelemetry terminology, "Autoinstrumentation" maps to what Application Insights calls "Codeless / Agent-based" instrumentation.

## Related Pages

- [[application-insights]] — service using instrumentation
- [[opentelemetry]] — related standard
- [[app-instrumentation]] — source page
- [[apm]] — broader context
