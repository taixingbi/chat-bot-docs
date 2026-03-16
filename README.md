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
Answer Generation
        │
   ┌────┴─────┐
   │          │
Online Eval   Offline Eval
   │              │
   │              ├─ Benchmark datasets
   │              ├─ Golden answers
   │              ├─ Retrieval recall@k
   │              ├─ LLM judge scoring
   │              └─ Regression tests
   │
   ├─ Latency
   ├─ Token usage
   ├─ User feedback
   ├─ Thumbs up/down
   └─ Hallucination detection
```
