# GCP – Monocloud Data Analytics Platform

This folder contains C4 diagram examples for a **data analytics platform** running entirely on **Google Cloud Platform (GCP)**.

## Architecture overview

| Layer | Technology choices |
|---|---|
| Event streaming | Cloud Pub/Sub |
| Batch ingestion | Cloud Composer (Airflow) |
| Stream processing | Cloud Dataflow (Apache Beam) |
| Raw / landing zone | Cloud Storage (GCS) |
| Curated & mart zones | BigQuery |
| Transformation | Cloud Dataflow, dbt on Cloud Run |
| ML pipelines | Vertex AI Pipelines |
| Feature store | Vertex AI Feature Store |
| Notebooks | Vertex AI Workbench |
| Data catalogue | Dataplex / Data Catalog |
| Analytics API | Cloud Run (FastAPI) |
| Identity & security | Cloud IAM, VPC Service Controls |
| Observability | Cloud Monitoring, Cloud Logging |

## Diagrams

| File | C4 Level | Description |
|---|---|---|
| [`context.puml`](context.puml) | Level 1 – Context | High-level actors and external systems |
| [`containers.puml`](containers.puml) | Level 2 – Containers | Runtime containers and their interactions |

## Rendering

```bash
java -jar plantuml.jar monocloud/gcp/context.puml
java -jar plantuml.jar monocloud/gcp/containers.puml
```

Online renderer: <https://www.plantuml.com/plantuml/uml/>
