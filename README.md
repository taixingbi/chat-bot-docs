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

A[Test Dataset]

A --> B[Eval Runner]

B --> C[API Gateway]

C --> D[Orchestrator / MCP Layer]

D --> E[RAG Retrieval Tool]
D --> F[MCP Tool Suite]

E --> G[Answer Generation]
F --> G

G --> H[Expected Answer]

H --> I[Evaluation Metrics]
```
