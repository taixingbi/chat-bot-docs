# chat-bot-docs

## High-Level Architecture

```mermaid
flowchart TD

subgraph Client
    Client[Client / UI]
end

subgraph API
    Gateway[API Gateway]
end

subgraph Core
    Orchestrator[Orchestrator / MCP Layer]
end

subgraph Tools
    Retrieval[RAG Retrieval Tool]
    Tools[MCP Tool Suite]
end

subgraph Response
    Answer[Answer Generation]
end

Client --> Gateway
Gateway --> Orchestrator

Orchestrator --> Retrieval
Orchestrator --> Tools

Retrieval --> Answer
Tools --> Answer
```
