# chat-bot-docs

### High-Level Diagram

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


### Test/Eval Diagram
## Test / Evaluation Flow

```mermaid
flowchart TD

Answer[Answer Generation]

Answer --> Online[Online Evaluation]
Answer --> Offline[Offline Evaluation]

Offline --> Dataset[Test Dataset]
Offline --> Judge[LLM Judge]
```
