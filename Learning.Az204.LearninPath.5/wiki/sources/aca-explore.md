---
title: "Explore Azure Container Apps"
type: source
tags: [container-apps, aca, microservices, dapr, keda, az204]
sources: [learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_2-explore-azure-container-apps.pdf]
created: 2026-06-16
updated: 2026-06-16
---

# Explore Azure Container Apps

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_2-explore-azure-container-apps.pdf

## Overview

[[azure-container-apps]] (ACA) enables running microservices and containerized applications on a **serverless platform** built on top of [[azure-kubernetes-service]]. It abstracts away Kubernetes management.

## Common Use Cases

- Deploying API endpoints
- Hosting background processing applications
- Handling event-driven processing
- Running microservices

## Key Capabilities

- Dynamic scaling based on: HTTP traffic, event-driven processing, CPU/memory load, or any **KEDA-supported scaler**.
- Most applications can **scale to zero** (except CPU/memory-based scaling).
- Run multiple container revisions and manage application lifecycle.
- Enable HTTPS ingress without managing other Azure infrastructure.
- Split traffic across versions for **Blue/Green deployments** and **A/B testing**.
- Built-in DNS-based service discovery for internal endpoints.
- Native **Dapr** integration for microservices.
- Run containers from any registry (Docker Hub, ACR, or private).
- Native **Azure Key Vault** secret integration.
- Monitor logs via **Azure Log Analytics**.

## Container Apps Environments

> [!source] learn.microsoft.com_en-us_training_modules_implement-azure-container-apps_2-explore-azure-container-apps.pdf
> "Individual container apps are deployed to a single Container Apps environment, which acts as a secure boundary around groups of container apps."

- Apps in the same environment share the same **virtual network** and **Log Analytics workspace**.
- Deploy to same environment when: managing related services, deploying to the same VNet, sharing Dapr config/components.
- Deploy to different environments when: ensuring compute isolation, preventing Dapr service invocation communication.

## Microservices Support

ACA provides: independent scaling, versioning, upgrades, service discovery, and native Dapr integration.

## Dapr Integration

[[dapr]] (Distributed Application Runtime) adds: observability, pub/sub, service-to-service invocation with mutual TLS, retries, and more on top of ACA's microservice building blocks.

## Related Pages

- [[azure-container-apps]] – entity page
- [[dapr]] – entity page
- [[keda]] – entity page
- [[container-apps-environment]] – concept page
- [[aca-containers]] – containers in ACA source
- [[aca-authentication]] – authentication source
- [[aca-revisions-secrets]] – revisions and secrets source
- [[aca-dapr]] – Dapr integration source
