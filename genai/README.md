# GenAI – LLM RAG Platform (Retrieval-Augmented Generation)

This folder contains C4 diagram examples for a **Retrieval-Augmented Generation (RAG) platform** that grounds LLM answers in a private organisational knowledge base.

## Architecture overview

```
User Query
    │
    ▼
Chat API ──► RAG Orchestrator ──► Query Expander
                │                      │
                │              Hybrid Retriever ──► Azure AI Search (vector + keyword)
                │                      │
                │              Reranker (cross-encoder)
                │                      │
                │              Prompt Builder ──► LLM API (GPT-4o / Gemini / Claude)
                │                      │
                │              Citation Extractor
                │                      │
                ◄─────── Response Streamer (SSE) ──► User
```

### RAG pipeline steps

1. **Query expansion**: Generate sub-queries and HyDE variants to improve retrieval recall.
2. **Semantic cache check**: Avoid redundant LLM calls for similar recent queries.
3. **Hybrid retrieval**: Combine keyword (BM25) and dense vector search for high-precision results.
4. **Cross-encoder reranking**: Re-score candidate passages to surface the most relevant context.
5. **Prompt construction**: Assemble context, history, and query within the LLM's token budget.
6. **LLM generation**: Call the hosted LLM to produce a grounded, cited answer.
7. **Guardrails**: Screen inputs and outputs for harmful content, PII, and prompt-injection.

## Technology choices

| Layer | Technology |
|---|---|
| Frontend | React SPA – Azure Static Web Apps |
| API gateway | Azure API Management |
| Chat API | Azure Container Apps (FastAPI) |
| RAG orchestration | LangChain / Semantic Kernel |
| LLM provider | Azure OpenAI (GPT-4o), switchable to Gemini / Claude |
| Embedding model | text-embedding-3-large (Azure OpenAI) |
| Vector store | Azure AI Search (hybrid + semantic reranker) |
| Document store | Azure Blob Storage |
| Metadata & history | Azure Cosmos DB |
| Semantic cache | Azure Cache for Redis |
| Evaluation | Azure PromptFlow |
| Observability | Azure Monitor + Application Insights |

## Diagrams

| File | C4 Level | Description |
|---|---|---|
| [`context.puml`](context.puml) | Level 1 – Context | High-level actors and external systems |
| [`containers.puml`](containers.puml) | Level 2 – Containers | Runtime containers and their interactions |
| [`components.puml`](components.puml) | Level 3 – Components | Internal components of the RAG Orchestrator |

## Rendering

```bash
java -jar plantuml.jar genai/context.puml
java -jar plantuml.jar genai/containers.puml
java -jar plantuml.jar genai/components.puml
```

Online renderer: <https://www.plantuml.com/plantuml/uml/>
