flowchart TD

    A([Start]) --> B[Setup Visibility & Connection System]

    B --> C[Visibility]

    C --> D[Identify People & Communities]

    D --> E[Send Connection / Engagement Request]

    E --> X[X (Twitter)]
    E --> L[LinkedIn]
    E --> R[Reddit]

    %% Observation Phase
    X --> X1[Observe High-Engagement Posts]
    L --> L1[Observe High-Engagement Posts]
    R --> R1[Observe High-Engagement Posts]

    %% Learning Phase
    X1 --> X2[Learn How People Structure Posts]
    L1 --> L2[Learn How People Structure Posts]
    R1 --> R2[Learn How People Structure Posts]

    %% Notes
    X2 --> X3[Write Notes on Format & Hooks]
    L2 --> L3[Write Notes on Format & Hooks]
    R2 --> R3[Write Notes on Format & Hooks]

    %% Merge Learnings
    X3 --> M[Content Patterns Identified]
    L3 --> M
    R3 --> M

    %% Creation Phase
    M --> N[Create Content]

    N --> O[Post on Platforms]

    O --> P[Measure Engagement & Responses]

    P --> Q[Refine Style & Messaging]

    %% Project Loop
    Q --> S[Lessons from Doing Projects]

    S --> T[Answer Core Questions]
    T --> T1[How to do it?]
    T --> T2[Best things learned?]
    T --> T3[Core concept?]

    T1 --> U[Convert Lessons into Content]
    T2 --> U
    T3 --> U

    U --> N
