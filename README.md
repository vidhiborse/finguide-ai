# FinGuide AI 🇮🇳
### India's AI-Powered Personal Finance Mentor
> ET AI Hackathon 2026 — Problem Statement 9: AI Money Mentor

[![Live Demo](https://finguide-ai-lemon.vercel.app/)]

---

## 🎯 Problem Statement
95% of Indians have no financial plan. Financial advisors charge ₹25,000+ per year and serve only HNIs. FinGuide AI gives every Indian a CFP-grade advisor — for free.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 💯 Money Health Score | 6-dimension financial wellness score across emergency fund, insurance, investments, debt, tax, retirement |
| 🔬 MF Portfolio X-Ray | Upload CAMS/KFintech PDF → true XIRR, overlap analysis, expense drag, AI rebalancing plan |
| 🔥 FIRE Path Planner | Goal-wise SIP roadmap with age-based asset allocation shifts |
| 📋 Tax Wizard | Old vs new regime comparison, 6 investment options ranked by risk and liquidity |
| 🎯 Life Event Advisor | Bonus, marriage, baby, job loss — personalised by tax bracket and risk profile |
| 💑 Couple's Money Planner | Joint HRA, NPS matching, SIP splits optimised across both incomes |
| 🛡️ Emergency Fund | Liquid fund recommendations with gap analysis |
| 🏖️ Retirement Planner | NPS + mutual fund corpus calculator |
| 📊 Expense Tracker | 12-category breakdown with AI insights |
| 🤖 AI Chatbot | Answers financial questions using your actual profile numbers |

---

## 🏗️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| Styling | CSS Variables + Responsive Grid |
| Auth & Database | Firebase Authentication + Firestore |
| AI Chatbot | Groq API (LLaMA 3.1) |
| Deployment | Vercel |

---

## 🚀 Setup Instructions

### Prerequisites
- Node.js 18+
- Firebase account (free)
- Groq API key (free)

### Installation
```bash
# Clone the repository
git clone https://github.com/YOUR-USERNAME/finguide-ai.git

# Enter project directory
cd finguide-ai

# Install dependencies
npm install

# Start development server
npm run dev
```

### Environment Setup

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable Authentication (Email/Password) and Firestore
3. Copy your Firebase config into `src/firebase.js`
4. Get a free Groq API key at [console.groq.com](https://console.groq.com)
5. Add your Groq key in `src/components/Chatbot.jsx`

### Build for Production
```bash
npm run build
```

---

## 📊 Impact Model

| Metric | Value |
|--------|-------|
| Target Users | 3 crore salaried Indians aged 25-45 |
| Tax savings per user | ₹18,000/year (unused 80C, 80D, NPS) |
| Expense ratio savings | ₹9,400/year (switching to index funds) |
| Advisor fee replaced | ₹25,000/year (CFP-equivalent advice) |
| **Total value per user** | **₹87,400/year** |

---

## 🏛️ Architecture
```
User → React Frontend → Firebase Auth → Dashboard
                      ↓
              Firestore Database (user profiles)
                      ↓
              Groq API (LLaMA 3.1) → AI Chatbot
                      ↓
              Financial Calculations (pure JS)
              XIRR · Tax · SIP · Health Score
```

---

## 👩‍💻 Built By
**Team FinGuide** — ET AI Hackathon 2026

*Every rupee saved. Every goal tracked. Every Indian deserves a financial mentor.*
```

Save this file then run:
```
git add README.md
git commit -m "Add README with setup instructions"
git push
