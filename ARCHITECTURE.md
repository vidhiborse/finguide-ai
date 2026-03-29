# FinGuide AI — Architecture Document

## System Overview

FinGuide AI is a three-layer system: React frontend, Firebase backend, and Groq AI layer.

---

## Architecture Diagram
```
┌─────────────────────────────────────────────────────────┐
│                     USER BROWSER                         │
│                                                          │
│  ┌─────────────┐    ┌──────────────┐   ┌─────────────┐  │
│  │  Auth Page  │    │  Landing /   │   │  Dashboard  │  │
│  │  Login /    │───▶│  Onboarding  │──▶│  10 Feature │  │
│  │  Signup     │    │  3-step form │   │  Pages      │  │
│  └─────────────┘    └──────────────┘   └─────────────┘  │
└─────────────────────────────────────────────────────────┘
         │                    │                   │
         ▼                    ▼                   ▼
┌─────────────────┐  ┌──────────────┐   ┌──────────────────┐
│ Firebase Auth   │  │  Firestore   │   │   Groq API       │
│                 │  │  Database    │   │   (LLaMA 3.1)    │
│ • Email/Pass    │  │              │   │                  │
│ • Password hash │  │ • User data  │   │ • AI Chatbot     │
│ • Forgot pass   │  │ • Goals      │   │ • Personalised   │
│ • Session mgmt  │  │ • Scores     │   │   responses      │
└─────────────────┘  └──────────────┘   └──────────────────┘
```

---

## Agent Roles

### 1. Financial Calculation Engine (Pure JavaScript)
All financial math runs in the browser — no server needed.
- **XIRR Calculator** — Iterative calculation on SIP cashflows
- **Tax Engine** — Old vs new regime with all 6 deduction sections
- **Money Health Score** — 6-dimension weighted scoring algorithm
- **SIP Projector** — Compound interest with monthly compounding
- **Asset Allocator** — Age-based equity/debt/gold split

### 2. Firebase Authentication Agent
- Handles signup, login, password reset
- Passwords hashed by Firebase (bcrypt) — never stored plain text
- Session persistence across browser refreshes

### 3. Firestore Database Agent
- Stores user financial profile after onboarding
- Auto-loads profile on next login (no re-entry needed)
- Real-time sync across devices

### 4. Groq AI Agent (LLaMA 3.1)
- Receives user financial profile as context
- Answers personalised financial questions
- Suggestion chips for common queries
- Error handling with graceful fallback messages

---

## Data Flow
```
1. User signs up → Firebase creates account (password hashed)
2. User fills 3-step onboarding → Data saved to Firestore
3. Dashboard loads → Financial calculations run in browser
4. User asks chatbot → Profile sent as context to Groq API
5. Groq returns answer → Displayed in chat UI
6. Next login → Profile auto-loaded from Firestore
```

---

## Tool Integrations

| Tool | Purpose | Free Tier |
|------|---------|-----------|
| Firebase Auth | Login/Signup | Yes — unlimited |
| Firestore | User data storage | Yes — 1GB free |
| Groq API | AI chatbot (LLaMA 3.1) | Yes — 14,400 req/day |
| Vercel | Hosting & deployment | Yes — unlimited |

---

## Error Handling

| Error | Handling |
|-------|---------|
| Wrong password | Specific Firebase error message shown |
| Groq API fails | "Connection error, try again" message |
| Network offline | Cached profile still shown |
| Invalid form data | Validation before each step with specific message |
| Expired session | Auto-redirect to login page |

---

## Security

- Passwords: Firebase bcrypt hashing
- API keys: Client-side (acceptable for hackathon — production would use backend proxy)
- Data: Each user can only access their own Firestore document (UID-based rules)
- HTTPS: Enforced by Vercel on all traffic
```
