# C4 Diagrams – Architecture Examples

This repository contains [C4 model](https://c4model.com/) diagram examples written in [PlantUML](https://plantuml.com/) using the [C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) library.

## Contents

| Folder | Description |
|---|---|
| [`monocloud/azure/`](monocloud/azure/) | **Azure** – E-Commerce Platform (microservices, event-driven) |
| [`monocloud/gcp/`](monocloud/gcp/) | **GCP** – Data Analytics Platform (data lake, ML/AI pipelines) |
| [`monocloud/aws/`](monocloud/aws/) | **AWS** – Serverless SaaS Platform (Lambda, DynamoDB, EventBridge) |
| [`multicloud/`](multicloud/) | **Multi-Cloud** – Financial Services Platform (Azure primary, AWS DR, GCP analytics) |
| [`genai/`](genai/) | **GenAI / LLM** – Retrieval-Augmented Generation (RAG) Platform |

## C4 diagram levels used

| Level | Diagram type | File |
|---|---|---|
| L1 | System Context | `context.puml` |
| L2 | Container | `containers.puml` |
| L3 | Component | `components.puml` (GenAI only) |

## Rendering diagrams

### Option 1 – Online

Paste the `.puml` content into <https://www.plantuml.com/plantuml/uml/>.

### Option 2 – VS Code

Install the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) and press **Alt+D** to preview.

### Option 3 – PlantUML JAR

```bash
# Download the JAR once
curl -Lo plantuml.jar https://github.com/plantuml/plantuml/releases/latest/download/plantuml.jar

# Render a single diagram
java -jar plantuml.jar monocloud/azure/context.puml

# Render all diagrams recursively
java -jar plantuml.jar "**/*.puml"
```

### Option 4 – Docker

```bash
docker run --rm -v "$(pwd):/data" plantuml/plantuml "**/*.puml"
```

## C4 model overview

```
Level 1 – Context   : Who uses the system and what does it interact with?
Level 2 – Container : What are the deployable units (apps, DBs, queues)?
Level 3 – Component : What are the major building blocks inside a container?
Level 4 – Code      : How do classes / functions implement a component?
```

See <https://c4model.com/> for the full specification.
