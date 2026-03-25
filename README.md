## Glutony

```mermaid 

flowchart TD
    A[Content Sources] --> B[Ingestion Layer]
    B --> C[Ephemeral Raw Buffer<br/>Redis TTL]
    C --> D[Normalization Layer]
    D --> E[Embedding + Similarity]
    E --> F[Topic Clustering]

    F --> G[Source Scoring Engine]
    G --> H[Representative Source Selection]

    H --> I[AI Synthesis Pipeline<br/>Summarize + Combine + Rewrite in French]
    I --> J[Compliance Layer]

    J --> K{Approval}
    K -->|Auto| L[Approved Content]
    K -->|Manual| M[Human Review]

    L --> N[Safe Content Store]
    M --> N

    N --> O[Issue Builder<br/>Newsletter JSON]
    O --> P[Template Engine]
    O --> Q[Admin Dashboard]

    P --> R[Email Rendering]
    Q --> R

    R --> S[Delivery Layer]
    S --> T[Webhook Events]
    T --> U[Analytics]

    U --> G
