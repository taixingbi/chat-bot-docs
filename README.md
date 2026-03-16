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

B[Online Evaluation]
C[Offline Evaluation]

%% Online metrics
B --> B1[Latency]
B --> B2[Token Usage]
B --> B3[User Feedback]
B --> B4[Thumbs Up / Down]
B --> B5[Hallucination Detection]

%% Offline metrics
C --> C1[Benchmark Datasets]
C --> C2[Golden Answers]
C --> C3[Retrieval Recall@K]
C --> C4[LLM Judge Scoring]
C --> C5[Regression Tests]
```
