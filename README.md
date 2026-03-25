## Glutony


flowchart TD

%% SOURCES
A[Content Sources<br/>RSS / APIs / Websites / URLs]

%% INGESTION
A --> B[Ingestion Layer<br/>Fetchers + Parsers]

%% TEMP RAW
B --> C[Ephemeral Raw Buffer<br/>Redis TTL - No long-term raw storage]

%% NORMALIZATION
C --> D[Normalization Layer<br/>Clean text / metadata extraction / canonical URL]

%% EMBEDDINGS + DEDUPE
D --> E[Embedding + Similarity Layer<br/>Near-duplicate detection]

%% CLUSTERING
E --> F[Topic Clustering Engine<br/>Group articles about same subject]

%% SOURCE SCORING
F --> G[Source Scoring Engine<br/>Trust / freshness / depth / originality / clarity]

%% REPRESENTATIVE SELECTION
G --> H[Representative Source Selection<br/>Pick top source(s) per cluster]

%% MULTI-SOURCE SYNTHESIS
H --> I[AI Content Pipeline<br/>- Expert summarization<br/>- Multi-source synthesis<br/>- Key points extraction<br/>- French-native rewrite<br/>- Title / deck / why it matters]

%% COMPLIANCE
I --> J[Compliance Layer<br/>Similarity / compression / attribution / risk score]

%% APPROVAL
J --> K{Approval Decision}
K -->|Low Risk| L[Auto Approved]
K -->|Flagged| M[Human Review Queue<br/>Approve / Edit / Reject]

%% SAFE STORE
L --> N[Safe Content Store<br/>Supabase Postgres]
M --> N

%% ISSUE BUILDING
N --> O[Issue Builder<br/>Generate newsletter JSON]

%% TEMPLATE + ADMIN
O --> P[Template System<br/>React Email Components]
O --> Q[Admin Dashboard<br/>Review / edit / preview / schedule]

%% RENDER
P --> R[Render Email HTML]
Q --> R

%% DELIVERY
R --> S[Delivery Layer<br/>Resend API]

%% WEBHOOKS
S --> T[Webhook Ingestion<br/>Opens / clicks / bounces / unsubscribes]

%% ANALYTICS
T --> U[Analytics & Reporting<br/>CTR / source performance / template performance / trend feedback]

%% FEEDBACK LOOP
U --> G
