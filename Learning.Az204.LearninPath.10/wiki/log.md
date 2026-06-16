---
title: "Wiki Activity Log"
type: synthesis
tags: [log, activity, az204, messaging]
sources: [index.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Activity Log

Related catalog: [[index]].

---

## [2026-06-16] ingest | AZ-204 Learning Path 10 — Azure Message Queues (6 PDFs)

**Raw sources processed:** 6 PDFs from Microsoft Learn module `discover-azure-message-queue`.

**Units ingested:**
1. Unit 2 — Choose a message queue solution
2. Unit 3 — Explore Azure Service Bus
3. Unit 4 — Discover Service Bus queues, topics, and subscriptions
4. Unit 5 — Explore Service Bus message payloads and serialization
5. Unit 7 — Explore Azure Queue Storage
6. Unit 8 — Create and manage Azure Queue Storage and messages by using .NET

**Files Added:**

*Sources (6):*
- `sources/choose-queue-solution.md`
- `sources/azure-service-bus-overview.md`
- `sources/service-bus-queues-topics-subscriptions.md`
- `sources/service-bus-message-payloads.md`
- `sources/azure-queue-storage-overview.md`
- `sources/queue-storage-dotnet.md`

*Entities (3):*
- `entities/azure-service-bus.md`
- `entities/azure-queue-storage.md`
- `entities/azure-storage-account.md`

*Concepts (8):*
- `concepts/queue-solution-decision.md`
- `concepts/service-bus-tiers.md`
- `concepts/service-bus-advanced-features.md`
- `concepts/service-bus-receive-modes.md`
- `concepts/publish-subscribe-pattern.md`
- `concepts/service-bus-message-structure.md`
- `concepts/amqp.md`
- `concepts/queue-storage-net-operations.md`

*Wiki root (2):*
- `index.md`
- `log.md`

**Files Updated:** None (initial ingest).

**Key Takeaways:**

- **Azure Service Bus** is the enterprise-grade choice: FIFO (via sessions), transactions, duplicate detection, dead-letter queue, topics/pub-sub, messages up to 100 MB (Premium). Use when message reliability and ordering are critical.
- **Azure Queue Storage** is the simple/scalable choice: unlimited queue size (80+ GB), server-side logging, per-message progress tracking. Use when simplicity and scale beat advanced messaging features.
- **Service Bus tiers**: Basic (queues only, 256 KB), Standard (topics + transactions, 256 KB), Premium (JMS 2.0, up to 100 MB, predictable latency, scaling).
- **Peek Lock** (two-stage receive) is the at-least-once delivery mode in Service Bus; **Receive and Delete** is the simpler but lossy mode.
- **Topics + subscriptions** enable pub/sub (1:n): each subscription gets a copy of every message; SQL filter rules narrow what each subscription receives.
- **AMQP 1.0** is the primary Service Bus wire protocol (open standard); compatible with ActiveMQ and RabbitMQ; binary encoding is not HTTP-friendly.
- **Queue Storage .NET SDK**: `QueueClient` class; two-step dequeue (`ReceiveMessages` → `DeleteMessage`) mirrors Service Bus Peek Lock; `UpdateMessage` extends visibility timeout for long-running tasks.
- **Message structure**: binary payload (opaque to broker) + broker properties (`MessageId`, `CorrelationId`, `SessionId`, `ReplyTo`, etc.) + user properties. `ContentType` describes the payload MIME type.

**Contradictions found:** None detected across the 6 source documents. The 64 KB Service Bus message size limit in the decision guide (unit 2) refers to the Basic/Standard tier; Premium supports up to 100 MB — this is consistent with the tier comparison in unit 3 and is not a contradiction, just a tier-dependent nuance.
