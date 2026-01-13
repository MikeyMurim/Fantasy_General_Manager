# Technical Design Document (RFC)

**Author:** Michael Murimbechi
**Date:** 13th January 2026

## 1. Context & Scope
Fantasy sports decisions are often emotional. This tool introduces objectivity by aggregating data and using AI for qualitative analysis. This MVP focuses solely on the **NBA**, with architectural room to expand to **English Premier League** 

## 2. System Architecture
The system follows a standard **Client-Server** architecture.
* **Client:** React Native (Expo) handles the UI and state management.
* **Server:** A stateless Python REST API handles data aggregation.
* **External:** The Python server acts as a proxy to both the NBA Data API and the OpenAI API.

## 3. Data Flow Strategy
To minimize latency and cost:
1.  **Fetch:** Python backend fetches raw stats from `nba_api`.
2.  **Filter:** Python processes this data (calculates averages, filters last 5 games) *before* sending it to the AI.
3.  **Synthesize:** The AI receives a lean, text-only summary of the stats to generate the narrative.
4.  **Present:** The Client receives a JSON object containing both the structured stats (for graphs) and the unstructured text (for reading).

## 4. Constraints (Expo Go)
Since the app runs on a physical device via Expo Go, it cannot resolve `localhost`.
* **Solution:** The API Client in React Native must be configured to point to the development machine's Local LAN IP 
## 5. Security & Costs
* **API Keys:** OpenAI keys are stored **only** on the backend (`.env` file). The frontend never accesses the OpenAI API directly.
* **Rate Limiting:** (Future Scope) Implement basic rate limiting to prevent API cost overruns.