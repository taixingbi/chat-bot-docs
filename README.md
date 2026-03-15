# chat-bot-docs


### high level architecture diagram

flowchart TD

Client[Client / UI]

Client --> Gateway[API Gateway]

Gateway --> Orchestrator[Orchestrator / MCP Layer]

Orchestrator --> Retrieval[RAG Retrieval Tool]
Orchestrator --> Tools[MCP Tool Suite]

Retrieval --> Answer[Answer Generation]
Tools --> Answer
