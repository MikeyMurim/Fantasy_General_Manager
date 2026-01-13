sequenceDiagram
    participant User
    participant App as React Native App
    participant Backend as Python FastAPI
    participant NBA as NBA API
    participant AI as OpenAI

    User->>App: Enters "LeBron" vs "Curry"
    User->>App: Taps "Analyze"
    App->>Backend: POST /analyze {players: [LeBron, Curry]}
    
    activate Backend
    Backend->>NBA: Fetch Stats (LeBron)
    Backend->>NBA: Fetch Stats (Curry)
    NBA-->>Backend: Returns Raw Game Logs
    
    Note over Backend: Calculate Avg Points, <br/>Rebounds, & Efficiency
    
    Backend->>AI: Send Prompt + Computed Stats
    AI-->>Backend: Returns Narrative (Markdown)
    
    Backend-->>App: JSON {stats: {...}, text: "..."}
    deactivate Backend
    
    App->>User: Displays Comparison Card