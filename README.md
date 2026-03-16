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

subgraph Offline Evaluation
C1[Benchmark Datasets]
C2[Golden Answers]
C3[Retrieval Recall@K]
C4[LLM Judge Scoring]
C5[Regression Tests]

C1 --> C2 --> C3 --> C4 --> C5
end

subgraph Online Evaluation
B1[Latency]
B2[Token Usage]
B3[User Feedback]
B4[Thumbs Up / Down]
B5[Hallucination Detection]

B1 --> B2 --> B3 --> B4 --> B5
end
```
