graph TD
    subgraph "Mobile Device (Expo Go)"
        UI[React Native UI]
        State[State Management]
    end

    subgraph "Local Dev Machine"
        API[FastAPI Server :8000]
        Logic[Trade Logic Engine]
    end

    subgraph "The Cloud"
        NBA[NBA Stats API]
        OpenAI[OpenAI GPT API]
    end

    UI -->|1. User Inputs Trade| State
    State -->|2. POST /analyze-trade| API
    API -->|3. Get Stats| NBA
    NBA -->|4. Return JSON Data| API
    API -->|5. Send Stats + Prompt| OpenAI
    OpenAI -->|6. Return Analysis| API
    API --x|7. Transform & Validate| Logic
    Logic -->|8. Return Structured Response| UI