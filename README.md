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

D --> D1[retriever → Prompt construction -> LLM call -> Output parser / response]

E --> E1[timeout]
E --> E2[tool failure]

B --> F[Log Storage]
C --> G[Metrics System]
D --> H[Tracing System]
E --> I[Alerting]

F --> J[Grafana Loki]
G --> K[Prometheus]
H --> L[Langsmith]
I --> M[PagerDuty / Alerts]
```

### k3s

```mermaid
flowchart LR

subgraph A[Mac mini - Control Plane]
A1[Ingress]
A2[Grafana]
A3[Prometheus]
A4[ArgoCD]
A5[API Gateway]
end

subgraph B[GPU Node 1]
B1[vLLM primary]
B2[Embedding service]
B3[GPU batch jobs]
end

subgraph C[GPU Node 2]
C1[vLLM secondary]
C2[RAG ingestion workers]
C3[Overflow / experiments]
end

A --> B
A --> C

```

### reliable design

#### 3-tier routing policy for model
* GPU1 local vLLM first 
* GPU2 local vLLM second (very large queue, e.g over 5, total 160 assuming inference batch 32)
* Cloud agent / OpenAI last for timeout, overload(over 10), or hard failure

#### Gateway

authentication (access control)

rate limit (5 requests / second / user, 60 requests / minute / user, Tokens per minute (TPM) 90 000)

request validation

### LLM workloads
1. vLLM continuous batching
 * higher GPU utilization (make close to 1, lile 0.9)
 * reduced latency
 * parallel requests
2. Horizontal scaling
