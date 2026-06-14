# AWS – Monocloud Serverless SaaS Platform

This folder contains C4 diagram examples for a **serverless SaaS platform** running entirely on **Amazon Web Services (AWS)**.

## Architecture overview

| Layer | Technology choices |
|---|---|
| CDN / Edge | Amazon CloudFront, AWS WAF |
| Frontend | React SPA (static assets on S3) |
| Identity | Amazon Cognito (User Pools + SAML/OIDC federation) |
| API layer | Amazon API Gateway (REST) |
| Compute | AWS Lambda (Node.js, Python) |
| Primary database | Amazon DynamoDB (multi-tenant) |
| Analytics database | Amazon Aurora Serverless (PostgreSQL) |
| Object storage | Amazon S3 (assets + exports) |
| Event bus | Amazon EventBridge |
| Queue | Amazon SQS |
| Secrets | AWS Secrets Manager |
| Observability | Amazon CloudWatch, AWS X-Ray |

## Diagrams

| File | C4 Level | Description |
|---|---|---|
| [`context.puml`](context.puml) | Level 1 – Context | High-level actors and external systems |
| [`containers.puml`](containers.puml) | Level 2 – Containers | Runtime containers and their interactions |

## Rendering

```bash
java -jar plantuml.jar monocloud/aws/context.puml
java -jar plantuml.jar monocloud/aws/containers.puml
```

Online renderer: <https://www.plantuml.com/plantuml/uml/>
