# Monocloud Examples

This folder contains C4 diagram examples for architectures deployed on a **single cloud provider**.

| Folder | Cloud | Use-case |
|---|---|---|
| [`azure/`](azure/) | Microsoft Azure | E-Commerce Platform (microservices, event-driven) |
| [`gcp/`](gcp/) | Google Cloud Platform | Data Analytics Platform (data lake, ML/AI) |
| [`aws/`](aws/) | Amazon Web Services | Serverless SaaS Platform (Lambda, DynamoDB) |

Each sub-folder contains:
- **`context.puml`** – Level 1 (System Context): actors and external systems
- **`containers.puml`** – Level 2 (Container): runtime containers and their interactions
- **`README.md`** – Architecture overview and technology choices
