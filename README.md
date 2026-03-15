# chat-bot-docs

## High-Level Architecture

```mermaid
flowchart TD

A[Client / UI]

A --> B[API Gateway]

B --> C[Orchestrator / MCP Layer]

C --> D[RAG Retrieval Tool]
C --> E[MCP Tool Suite]

D --> F[Answer Generation]
E --> F

```
