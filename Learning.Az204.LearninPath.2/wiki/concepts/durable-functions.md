---
title: "Durable Functions"
type: concept
tags: [azure-functions, durable-functions, orchestration, stateful, az204]
sources: [learn.microsoft.com_en-us_training_modules_explore-azure-functions_2-azure-functions-overview.pdf,
          learn.microsoft.com_en-us_training_modules_explore-azure-functions_3-compare-azure-functions-hosting-options.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Durable Functions

## Definition

**Durable Functions** is an extension of [[azure-functions]] that enables writing stateful, long-running **orchestrations** in code (imperative approach). It extends Functions with the concept of orchestrator functions, activity functions, and entity functions.

## Purpose

- Create complex orchestrations by writing code (as opposed to Logic Apps' declarative GUI).
- Handle workflows that exceed the normal function timeout limits.
- Support fan-out/fan-in, async HTTP APIs, monitoring, and human-interaction patterns.

## Relevance to Hosting Plans

- The **Dedicated plan** description notes it is "best for long-running scenarios where Durable Functions **can't** be used" — implying Durable Functions is preferred for long-running orchestrations on other plans.
- HTTP triggered functions have a 230-second hard cap; Durable Functions async pattern can work around this for long-running HTTP scenarios.

## Comparison with Logic Apps

| Aspect | Durable Functions | Azure Logic Apps |
|--------|-----------------|-----------------|
| Orchestration style | Code-first (imperative) | Designer-first (declarative) |
| Language | C#, JavaScript, Python, etc. | JSON workflow definitions / GUI |
| Statefulness | Built-in via checkpointing | Built-in |

## Related Pages

- [[azure-functions]] – parent service
- [[azure-logic-apps]] – declarative orchestration alternative
- [[functions-hosting-plans]] – hosting context
- [[serverless-computing]] – broader concept
- [[discover-azure-functions]] – source
- [[compare-azure-functions-hosting-options]] – source
