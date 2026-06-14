# Multi-Cloud – Financial Services Platform

This folder contains C4 diagram examples for a **financial services platform** distributed across three cloud providers for resilience, compliance, and specialisation:

| Cloud | Role |
|---|---|
| **Azure** (West Europe) | Primary region – core banking, payments, identity |
| **AWS** (eu-west-1) | Disaster recovery / hot standby |
| **GCP** (europe-west4) | Analytics, ML/AI, and regulatory reporting |

## Why multi-cloud?

- **Resilience**: Active-active or active-passive DR between Azure and AWS avoids vendor lock-in for critical workloads.
- **Best-of-breed services**: GCP Vertex AI and BigQuery are used for fraud detection and analytics without migrating the entire platform.
- **Regulatory compliance**: Data residency and sovereign-cloud constraints can be met per workload.

## Architecture overview

```
                  ┌─────────────────────────────────────────────────────┐
Internet ──HTTPS──► Azure (Primary)                                     │
                  │  API Gateway → Core Banking → Azure SQL Hyperscale  │
                  │  Payments → SWIFT                                    │
                  │  Event Store ─────────────────────────┐             │
                  └───────────────────────────────────────┼─────────────┘
                                                          │ Event replication
                  ┌───────────────────────────────────────▼─────────────┐
                  │ GCP (Analytics & AI)                                │
                  │  Dataflow → BigQuery Data Lake                      │
                  │  Vertex AI Fraud Detection  ◄── Azure Payments      │
                  │  Cloud Run Regulatory Reporting → Regulator         │
                  └─────────────────────────────────────────────────────┘
                                                  ▲
                  ┌───────────────────────────────┼─────────────────────┐
                  │ AWS (DR / Secondary)          │ Failover traffic    │
                  │  NLB + Route 53               │                     │
                  │  EKS Core Banking (standby)   │                     │
                  │  Aurora PostgreSQL (replica)   │                     │
                  └─────────────────────────────────────────────────────┘
```

## Diagrams

| File | C4 Level | Description |
|---|---|---|
| [`context.puml`](context.puml) | Level 1 – Context | High-level actors and external systems |
| [`containers.puml`](containers.puml) | Level 2 – Containers | Cross-cloud containers and their interactions |

## Rendering

```bash
java -jar plantuml.jar multicloud/context.puml
java -jar plantuml.jar multicloud/containers.puml
```

Online renderer: <https://www.plantuml.com/plantuml/uml/>
