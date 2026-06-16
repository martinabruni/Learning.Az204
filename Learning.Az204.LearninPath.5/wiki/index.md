---
title: "Wiki Index – AZ-204 Learning Path 5: Containerized Solutions"
type: synthesis
tags: [index, az204, containers, aci, aca, acr]
sources: [aci-overview.md, aca-explore.md, acr-overview.md]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Index — AZ-204 Learning Path 5: Containerized Solutions

This wiki is built from the 13 PDFs in `raw/`, covering three Microsoft Learn modules on Azure container technologies: Azure Container Instances (ACI), Azure Container Apps (ACA), and Azure Container Registry (ACR).
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-container-instances]] | Managed service to run isolated containers in Azure without VMs, billed per-second |
| [[azure-container-apps]] | Serverless container platform on top of AKS for microservices and event-driven apps |
| [[azure-container-registry]] | Managed private container registry based on Docker Registry 2.0; three service tiers |
| [[dapr]] | Open-source CNCF runtime providing pub/sub, service invocation, state management for microservices |
| [[azure-files]] | Fully managed cloud file shares via SMB; used as persistent volume in ACI containers |
| [[azure-kubernetes-service]] | Managed Kubernetes service; underlies ACA; recommended for full orchestration over ACI |

---

## Concepts

| Page | Summary |
|------|---------|
| [[container-group]] | Top-level ACI resource — containers sharing host, network, lifecycle, and storage |
| [[restart-policy]] | ACI restart options: Always (default), Never, OnFailure; enables run-once task pattern |
| [[secure-environment-variables]] | ACI env vars using `secureValue` — name visible, value hidden in portal/CLI |
| [[persistent-storage-containers]] | Mounting external volumes (Azure Files, secrets, empty dir, git repo) to stateless containers |
| [[container-apps-environment]] | Secure boundary around ACA apps sharing VNet and Log Analytics workspace |
| [[container-app-revisions]] | Immutable ACA version snapshots enabling traffic splitting for Blue/Green and A/B deployments |
| [[federated-identity]] | ACA built-in EasyAuth with Microsoft, GitHub, Google, Facebook, X, and OpenID Connect |
| [[sidecar-pattern]] | Helper container co-located with primary app sharing disk, network, and lifecycle |
| [[pub-sub-pattern]] | Messaging pattern enabling decoupled communication via Dapr and a message broker |
| [[acr-tasks-concept]] | ACR automation suite: quick builds, source/base-image/schedule triggers, multi-step YAML workflows |
| [[dockerfile]] | Script of layered instructions (FROM, WORKDIR, COPY, EXPOSE, CMD) for building container images |

---

## Sources — Module 1: Azure Container Instances

| Page | PDF |
|------|-----|
| [[aci-overview]] | `create-run-container-images-azure-container-instances_2-azure-container-instances-overview.pdf` |
| [[aci-restart-policies]] | `create-run-container-images-azure-container-instances_4-run-containerized-tasks-restart-policies.pdf` |
| [[aci-environment-variables]] | `create-run-container-images-azure-container-instances_5-set-environment-variables-azure-container-instances.pdf` |
| [[aci-azure-file-share-mount]] | `create-run-container-images-azure-container-instances_6-mount-azure-file-share-azure-container-instances.pdf` |

## Sources — Module 2: Azure Container Apps

| Page | PDF |
|------|-----|
| [[aca-explore]] | `implement-azure-container-apps_2-explore-azure-container-apps.pdf` |
| [[aca-containers]] | `implement-azure-container-apps_4-container-apps-containers.pdf` |
| [[aca-authentication]] | `implement-azure-container-apps_5-container-apps-authentication.pdf` |
| [[aca-revisions-secrets]] | `implement-azure-container-apps_6-container-apps-revisions-secrets.pdf` |
| [[aca-dapr]] | `implement-azure-container-apps_7-explore-distributed-application-runtime.pdf` |

## Sources — Module 3: Azure Container Registry

| Page | PDF |
|------|-----|
| [[acr-overview]] | `publish-container-image-to-azure-container-registry_2-azure-container-registry-overview.pdf` |
| [[acr-storage]] | `publish-container-image-to-azure-container-registry_3-azure-container-registry-storage.pdf` |
| [[acr-tasks]] | `publish-container-image-to-azure-container-registry_4-azure-container-registry-tasks.pdf` |
| [[dockerfile-components]] | `publish-container-image-to-azure-container-registry_5-dockerfile-components.pdf` |

---

## Page Counts

- Sources: 13
- Entities: 6
- Concepts: 11
- **Total wiki pages: 30** (plus this index and log.md)
