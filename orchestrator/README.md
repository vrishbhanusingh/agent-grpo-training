# Agentic Workflow Diagram

The following diagram illustrates the high-level agentic workflow and message flow for this component:

```mermaid
flowchart TD
    subgraph Message_Bus[Message Bus (RabbitMQ)]
        direction TB
        TaskQ[Task Queue]
        ResponseQ[Response Queue]
        RewardQ[Reward Queue]
    end

    UserInput[User/Input Source] -->|Task| TaskQ
    TaskQ -->|Task| SmallModelAgent[Small Model Agent]
    SmallModelAgent -->|Response| ResponseQ
    ResponseQ -->|Response| ScoringAgent[Scoring Agent (Big Model)]
    ScoringAgent -->|Reward| RewardQ
    RewardQ -->|Reward| SmallModelAgent
    SmallModelAgent -->|Log| LogFile[Logs/agent_interactions.jsonl]
    ScoringAgent -->|Log| LogFile
    Orchestrator[Orchestrator/Controller] -- Coordinates --> TaskQ
    Orchestrator -- Monitors --> ResponseQ
    Orchestrator -- Monitors --> RewardQ
    Orchestrator -- Logs --> LogFile
    LogFile -->|Training Data| Trainer[Trainer Service]
    Trainer -->|New Adapter| AdapterRegistry[Adapter Registry]
    AdapterRegistry --> Orchestrator
```

---
