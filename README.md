# Fantasy GM: AI-Powered Trade Assistant

![React Native](https://img.shields.io/badge/React_Native-Expo_Go-blue?logo=react)
![Python](https://img.shields.io/badge/Backend-FastAPI-009688?logo=fastapi)
![AI](https://img.shields.io/badge/AI-OpenAI_GPT--4-412991?logo=openai)

**Fantasy GM** is a mobile application that helps fantasy sports players make data-driven trade decisions. By combining real-time sports statistics with Large Language Model (LLM) reasoning, it acts as an unbiased analyst, evaluating trades based on schedule difficulty, injury risk, and statistical trends.

---

## Requirements

### 1. Functional Requirements (FRs)
* **FR-01:** Users must be able to input two player names (one to receive, one to give).
* **FR-02:** The system must fetch real-time "Last 5 Games" statistics for both players from an external sports API.
* **FR-03:** The system must generate a text-based analysis explaining the pros and cons of the trade.
* **FR-04:** The system must provide a clear "Accept" or "Reject" recommendation.

### 2. Non-Functional Requirements (NFRs)
* **NFR-01 (Performance):** The full analysis (API fetch + AI generation) must complete in under 5 seconds.
* **NFR-02 (Compatibility):** The frontend must run on iOS and Android devices via Expo Go.
* **NFR-03 (Reliability):** The backend must handle errors gracefully (e.g., if a player name is misspelled) without crashing the app.

### 3. User Stories
| ID | As a... | I want to... | So that... |
| :--- | :--- | :--- | :--- |
| **US-1** | Fantasy Manager | Compare two players side-by-side | I can see who has better raw stats. |
| **US-2** | Casual Fan | Get an AI explanation of the trade | I understand the context beyond just the numbers. |
| **US-3** | Mobile User | See a visual "Win Probability" score | I can make a quick decision at a glance. |

### 4. Fit Criteria (Acceptance Tests)
* **FC-1:** Given a trade of "LeBron James" for a bench player, the system returns a "REJECT" recommendation with >90% confidence.
* **FC-2:** If the user inputs a non-existent player, the UI displays a "Player not found" error message.
* **FC-3:** The API response payload adheres strictly to the JSON schema defined in `DESIGN.md`.

---

## 🛠 Tech Stack
* **Frontend:** React Native (TypeScript) with Expo.
* **Backend:** Python 3.10+ using FastAPI.
* **AI Engine:** OpenAI API (Model: `gpt-4o-mini`).
* **Data Source:** `nba_api` (Python Client).

##  Getting Started