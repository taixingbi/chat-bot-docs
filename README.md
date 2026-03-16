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

A[Online Evaluation]

A --> B1[Latency Metrics]
A --> B2[Token Usage]
A --> B3[User Feedback]
A --> B4[Thumbs Up / Down]
A --> B5[Hallucination Detection]
```


```mermaid
flowchart TD

A[Offline Evaluation]

A --> B1[Benchmark Datasets]
A --> B2[Golden Answers]
A --> B3[Retrieval Recall@K]
A --> B4[LLM Judge Scoring]
A --> B5[Regression Tests]
```

### SRE
```mermaid
flowchart LR

A[Telemetry Collection]

A --> B[Logs]
A --> C[Metrics]
A --> D[Traces]
A --> E[Errors]

B --> B1[request_id]
B --> B2[prompt]
B --> B3[model]
B --> B4[response]

C --> C1[latency_ms]
C --> C2[token_input]
C --> C3[token_output]
C --> C4[cost]

D --> D1[gateway → retriever → LLM]

E --> E1[timeout]
E --> E2[tool failure]

B --> F[Log Storage]
C --> G[Metrics System]
D --> H[Tracing System]
E --> I[Alerting]

F --> J[Grafana Loki]
G --> K[Prometheus]
H --> L[Jaeger / Tempo]
I --> M[PagerDuty / Alerts]
```
