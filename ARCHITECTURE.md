# System Architecture

## 1. Overview
The prototype has five conceptual layers: synthetic data; predictive analytics; evidence retrieval; agent orchestration; and the application interface. This is a component-level view, not a verified code-dependency diagram. Update it after the source archive has been extracted and inspected.

## 2. High-level architecture

```mermaid
flowchart TB
    U[Research user / reviewer] --> UI[React + TypeScript interface]
    UI --> API[FastAPI application]

    subgraph DATA[Data layer]
      P[5,000 synthetic patient records]
      O[53,550 longitudinal observations]
      KB[Clinical and rehabilitation documents]
    end

    subgraph ML[Predictive analytics]
      PRE[Validation and preprocessing]
      SPLIT[Patient-level train / validation / test split]
      TRAIN[Model training and tuning]
      EVAL[AUROC, AUPRC, calibration and error analysis]
      XAI[Feature importance and SHAP]
      OUT[Exploratory prediction outputs]
      P --> PRE
      O --> PRE
      PRE --> SPLIT --> TRAIN --> EVAL
      TRAIN --> XAI
      EVAL --> OUT
    end

    subgraph AGENT[Evidence and agent layer]
      ING[Document ingestion and chunking]
      VDB[(PostgreSQL + pgvector)]
      RET[Evidence retrieval]
      LG[LangGraph workflow]
      LLM[Local LLM via Ollama]
      CHECK[Passage checks and missing-information prompts]
      RESP[Evidence-linked response]
      KB --> ING --> VDB
      LG --> RET
      VDB --> RET
      RET --> LG
      LG --> LLM --> CHECK
      RET --> CHECK --> RESP
    end

    OUT --> API
    API --> LG
    RESP --> API
```

## 3. Predictive modelling flow

```mermaid
flowchart TD
    A[Synthetic patient and observation data]
    B[Define outcome and prediction time]
    C[Validate features and missingness]
    D[Split by patient identifier]
    E[Training data]
    F[Grouped cross-validation and tuning]
    G[Candidate models]
    H[Held-out test evaluation]
    I[Explainability and error review]
    J[Report metrics with limitations]
    A --> B --> C --> D --> E --> F --> G --> H --> I --> J
```

Candidate algorithms reported: Logistic Regression, Random Forest and Histogram-based Gradient Boosting. Logistic Regression is the selected model reported for both current test results. Exact preprocessing, feature lists, tuning spaces, thresholds and random seeds must be recorded from the implementation before claiming independent reproducibility.

## 4. Evidence-assisted interaction

```mermaid
sequenceDiagram
    actor User
    participant UI as React UI
    participant API as FastAPI
    participant Agent as LangGraph
    participant DB as PostgreSQL / pgvector
    participant LLM as Ollama
    User->>UI: Submit a research question
    UI->>API: Send request
    API->>Agent: Start workflow
    Agent->>DB: Retrieve relevant passages
    DB-->>Agent: Passages and metadata
    Agent->>LLM: Generate using retrieved context
    LLM-->>Agent: Draft response
    Agent->>Agent: Check support and missing information
    Agent-->>API: Response or clarification
    API-->>UI: Return response and sources
    UI-->>User: Display for human review
```

## 5. Technology map

| Layer | Reported technology | Responsibility |
|---|---|---|
| Data science | Python, scikit-learn | Data processing and modelling |
| Explainability | SHAP | Model-behaviour inspection |
| API | FastAPI | Backend interface |
| Frontend | React, TypeScript | User interface |
| Orchestration | LangGraph | Multi-step agent workflow |
| Local inference | Ollama | Local LLM runtime |
| Evidence store | PostgreSQL, pgvector | Document embeddings and retrieval |

## 6. Trust boundaries
- Synthetic data only; do not add identifiable patient information.
- LLM output is assistance, not authority.
- Display retrieved source passages and metadata where available.
- Citation checks do not guarantee factual or clinical correctness.
- Missing or ambiguous information should trigger clarification.
- Human review is required for every output.
- No connection to live clinical workflows without governance, security review, validation and institutional approval.

## 7. Details to add after source inspection
Document actual API routes, database schema, embedding model, chunking strategy, LLM version, agent state and transitions, preprocessing modules, model artefact format, deployment configuration and authentication controls.
