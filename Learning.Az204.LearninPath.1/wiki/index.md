---
title: "Wiki Index – AZ-204 Learning Path 1: Azure App Service"
type: synthesis
tags: [index, az204, app-service]
sources: [configure-web-app-settings-introduction.md, intro-app-service-introduction.md, scale-apps-introduction.md, deployment-slots-introduction.md]
created: 2025-01-15
updated: 2026-05-15
---

# Wiki Index — AZ-204 Learning Path 1: Azure App Service

This wiki is built from the 23 PDFs in `raw/`, covering four Microsoft Learn modules on Azure App Service.
Activity timeline: [[log]].

---

## Entities

| Page | Summary |
|------|---------|
| [[azure-app-service]] | Fully managed PaaS platform for web apps, mobile back ends, and APIs |
| [[app-service-plan]] | Compute resource plan defining OS, region, instance size, and pricing tier |
| [[deployment-slot]] | Live staging environment for zero-downtime blue-green deployments |
| [[autoscale]] | Rules-based automatic horizontal scaling of App Service instances |
| [[app-service-environment]] | Single-tenant Isolated-tier deployment inside an Azure Virtual Network |

---

## Concepts

| Page | Summary |
|------|---------|
| [[application-settings]] | Encrypted environment variables injected at app startup; support slot stickiness |
| [[general-settings]] | Stack, platform, and debugging settings (Always On, HTTP/2, ARR Affinity, etc.) |
| [[path-mappings]] | IIS handler mappings and virtual directory/storage mount configuration |
| [[diagnostic-logging]] | Built-in log types: application, web server, detailed errors, failed-request tracing |
| [[security-certificates]] | TLS/SSL certificate options: managed, purchased, Key Vault, upload (private/public) |
| [[authentication-authorization]] | EasyAuth: built-in federated identity with Entra ID, Google, GitHub, and others |
| [[networking-features]] | Inbound and outbound network traffic control features |
| [[container-deployment]] | Docker container deployment from ACR or Docker Hub on Windows and Linux |
| [[autoscale-conditions-rules]] | Metric-based and schedule-based autoscale conditions and rule anatomy |
| [[autoscale-best-practices]] | Guidelines to prevent oscillation, runaway scaling, and incorrect thresholds |
| [[slot-swapping]] | Zero-downtime swap mechanism; swap variants; swapped vs. sticky settings |
| [[traffic-routing]] | A/B traffic split between slots using percentage routing or query parameters |

---

## Sources — Module 1: Configure Web App Settings

| Page                                        | PDF                                                                |
| ------------------------------------------- | ------------------------------------------------------------------ |
| [[configure-web-app-settings-introduction]] | `configure-web-app-settings_1-introduction.pdf`                    |
| [[configure-application-settings]]          | `configure-web-app-settings_2-configure-application-settings.pdf`  |
| [[configure-general-settings]]              | `configure-web-app-settings_3-configure-general-settings.pdf`      |
| [[configure-path-mappings]]                 | `configure-web-app-settings_4-configure-path-mappings.pdf`         |
| [[enable-diagnostic-logging]]               | `configure-web-app-settings_5-enable-diagnostic-logging.pdf`       |
| [[configure-security-certificates]]         | `configure-web-app-settings_6-configure-security-certificates.pdf` |

## Sources — Module 2: Introduction to Azure App Service

| Page | PDF |
|------|-----|
| [[intro-app-service-introduction]] | `introduction-to-azure-app-service_1-introduction.pdf` |
| [[examine-azure-app-service]] | `introduction-to-azure-app-service_2-azure-app-service.pdf` |
| [[examine-app-service-plans]] | `introduction-to-azure-app-service_3-azure-app-service-plans.pdf` |
| [[deploy-code-to-app-service]] | `introduction-to-azure-app-service_4-deploy-code-to-app-service.pdf` |
| [[authentication-authorization-app-service]] | `introduction-to-azure-app-service_5-authentication-authorization-app-service.pdf` |
| [[network-features-app-service]] | `introduction-to-azure-app-service_6-network-features.pdf` |
| [[exercise-deploy-containerized-app]] | `introduction-to-azure-app-service_7-exercise-deploy-containerized-app.pdf` |

## Sources — Module 3: Scale Apps in App Service

| Page | PDF |
|------|-----|
| [[scale-apps-introduction]] | `scale-apps-app-service_1-introduction.pdf` |
| [[autoscale-factors]] | `scale-apps-app-service_2-autoscale-factors.pdf` |
| [[autoscale-conditions-rules-source]] | `scale-apps-app-service_3-app-service-autoscale-conditions-rules.pdf` |
| [[enable-autoscale-app-service]] | `scale-apps-app-service_4-autoscale-app-service.pdf` |
| [[autoscale-best-practices-source]] | `scale-apps-app-service_5-autoscale-best-practices.pdf` |

## Sources — Module 4: Deployment Slots

| Page | PDF |
|------|-----|
| [[deployment-slots-introduction]] | `understand-app-service-deployment-slots_1-introduction.pdf` |
| [[staging-environments]] | `understand-app-service-deployment-slots_2-app-service-staging-environments.pdf` |
| [[slot-swapping-mechanics]] | `understand-app-service-deployment-slots_3-app-service-slot-swapping.pdf` |
| [[swap-deployment-slots]] | `understand-app-service-deployment-slots_4-swap-deployment-slots.pdf` |
| [[route-traffic-app-service]] | `understand-app-service-deployment-slots_5-route-traffic-app-service.pdf` |

---

## Page Counts

- Sources: 23
- Entities: 5
- Concepts: 12
- **Total wiki pages: 40** (plus this index and log.md)
