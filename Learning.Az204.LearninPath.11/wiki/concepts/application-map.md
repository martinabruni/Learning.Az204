---
title: "Application Map"
type: concept
tags: [application-map, application-insights, distributed-apps, microservices, topology, az204]
sources: [application-map-source.md]
created: 2026-06-16
updated: 2026-06-16
---

# Application Map

## Definition

Application Map is a feature of [[application-insights]] that provides a **high-level, top-down visual view** of a distributed application's architecture. It helps spot performance bottlenecks or failure hotspots across all components.

## How It Works

- Each **node** represents an application component or its dependencies.
- Each node displays **health KPIs and alert status**.
- The map discovers components by following **HTTP dependency calls** between servers that have the Application Insights SDK installed.
- Uses the **cloud role name** property to identify components; this can be manually overridden.

## Progressive Discovery

1. On first load, queries are triggered to discover all related components.
2. A counter in the top-left corner shows discovered components.
3. "Update map components" refreshes to include all components found so far.
4. For apps where all components are roles in a single Application Insights resource, discovery is skipped.

## Components vs. External Dependencies

| Category | Examples | Characteristics |
|----------|---------|-----------------|
| Components | App microservices, worker roles | Code-level visibility; telemetry access |
| Observed external dependencies | SQL, Event Hubs | Team may not have code/telemetry access |

## Capabilities

- Drill into any component for detailed diagnostics (Application Insights events).
- For Azure services, drill into Azure diagnostics (e.g., SQL Database Advisor).
- Navigate to **performance and failure triage** for each component.
- Visualize topologies with **hundreds of components** across multiple levels.
- Components can span different Application Insights resources or subscriptions.

## Related Pages

- [[application-insights]] — entity page
- [[application-map-source]] — source page (unit 6)
- [[distributed-tracing]] — related concept
- [[availability-tests]] — shown on Application Map as a node
- [[apm]] — broader monitoring context
