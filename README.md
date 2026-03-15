# chat-bot-docs


### high level architecture diagram

User[Client / UI]

User --> Gateway[API Gateway]

Gateway --> Orchestrator[Orchestrator / MCP Layer]

Orchestrator --> Retrieval[RAG Retrieval Tool]

Retrieval --> Hybrid[Hybrid Search<br/>Dense + BM25]
Hybrid --> Rerank[Reranker]

Rerank --> VectorDB[Vector DB<br/>Embeddings]
Hybrid --> KeywordDB[Keyword / BM25 Index]

Orchestrator --> Tools[MCP Tool Suite]

Tools --> Models[Model Services<br/>LLM / Embedding]

VectorDB --> Answer[Answer Generation]
Models --> Answer
