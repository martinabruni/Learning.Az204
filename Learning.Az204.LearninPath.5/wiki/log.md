---
title: "Wiki Log – AZ-204 Learning Path 5"
type: synthesis
tags: [log, az204, containers]
created: 2026-06-16
updated: 2026-06-16
---

# Wiki Log — AZ-204 Learning Path 5

Chronological, append-only log of all wiki activity.

---

## [2026-06-16] ingest | AZ-204 LP5 – All 13 PDFs (Containerized Solutions)

- Added:
  - **Sources (13):** aci-overview.md, aci-restart-policies.md, aci-environment-variables.md, aci-azure-file-share-mount.md, aca-explore.md, aca-containers.md, aca-authentication.md, aca-revisions-secrets.md, aca-dapr.md, acr-overview.md, acr-storage.md, acr-tasks.md, dockerfile-components.md
  - **Entities (6):** azure-container-instances.md, azure-container-apps.md, azure-container-registry.md, dapr.md, azure-files.md, azure-kubernetes-service.md
  - **Concepts (11):** container-group.md, restart-policy.md, secure-environment-variables.md, persistent-storage-containers.md, container-apps-environment.md, container-app-revisions.md, federated-identity.md, sidecar-pattern.md, pub-sub-pattern.md, acr-tasks-concept.md, dockerfile.md
  - **Index:** index.md
  - **Log:** log.md
- Updated: (none — initial ingest)
- Key takeaways:
  - **ACI** is the fastest path to running isolated containers in Azure (seconds startup, per-second billing); supports restart policies for run-once tasks and Azure Files mounts for persistence (Linux only, must run as root).
  - **ACA** is a serverless container platform on AKS for microservices; supports KEDA-based scaling to zero, Blue/Green deployments via revisions, built-in EasyAuth with 6 identity providers, and native Dapr integration.
  - **ACR** is the private container registry with three tiers (Basic/Standard/Premium); Premium adds geo-replication, zone redundancy, and content trust. ACR Tasks automates the full build/test/push lifecycle triggered by code commits, base image changes, or schedules.
  - **Dockerfile** instructions (FROM, WORKDIR, COPY, EXPOSE, CMD) build layered images; EXPOSE is metadata only and does not publish ports.
  - **AKS** underlies ACA and is recommended over ACI when full orchestration is needed.
