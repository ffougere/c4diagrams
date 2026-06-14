# Azure – Monocloud E-Commerce Platform

This folder contains C4 diagram examples for an **e-commerce platform** running entirely on **Microsoft Azure**.

## Architecture overview

| Layer | Technology choices |
|---|---|
| CDN / Edge | Azure Front Door, Azure CDN |
| Frontend | React SPA (static assets on Blob Storage) |
| API gateway | Azure API Management |
| Microservices | Azure Container Apps |
| Databases | Azure Cosmos DB (catalogue), Azure SQL (orders, users) |
| Cache | Azure Cache for Redis |
| Search | Azure AI Search (Cognitive Search) |
| Messaging | Azure Service Bus |
| Identity | Azure AD B2C |
| Secrets | Azure Key Vault |
| Observability | Azure Monitor + Application Insights |

## Diagrams

| File | C4 Level | Description |
|---|---|---|
| [`context.puml`](context.puml) | Level 1 – Context | High-level actors and external systems |
| [`containers.puml`](containers.puml) | Level 2 – Containers | Runtime containers and their interactions |

## Rendering

Use [PlantUML](https://plantuml.com/) or the [C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) VS Code extension to render `.puml` files.

```bash
# Example: render with the PlantUML JAR
java -jar plantuml.jar monocloud/azure/context.puml
java -jar plantuml.jar monocloud/azure/containers.puml
```

You can also paste the content directly into <https://www.plantuml.com/plantuml/uml/>.
