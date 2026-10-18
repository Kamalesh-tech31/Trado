# Trado

A virtual stock trading platform for the Indian market. Practice trading Nifty stocks with simulated money, track your portfolio, and get risk analysis, AI-generated reports and learning content.

**Live demo:** https://trado-6e83.onrender.com

## Features

- **Accounts:** registration, login, OTP email verification, password reset, Google sign-in, user onboarding and investor profile
- **Market dashboard:** 25 NSE (Nifty) stocks with search, sector filter, current quotes, 7-day history charts and market-state indicators
- **Virtual trading:** start with ₹10,00,000 in simulated capital; buy and sell stocks, with holdings, wallet and transaction history saved per user
- **Portfolio risk analytics:** beta, volatility, max drawdown, VaR, Sharpe, Sortino, Treynor ratio, sector allocation, concentration (HHI) and health scores
- **Recommendations:** rule-based suggestions (for example, warnings for high sector concentration, a single stock above 30% of the portfolio, high portfolio beta or too few holdings)
- **AI features:**
  - Portfolio reports and a portfolio-aware chatbot (Groq, Llama 3.3 70B)
  - Learning notes and quizzes (Google Gemini)
- **Reports:** PDF export of portfolio reports
- **Learning:** lessons with progress tracking and a final assessment

## How it works

- **Market data:** quotes and history come from Yahoo Finance, polled by the frontend every 30 seconds. This is polling, not a live streaming feed.
- **Portfolio analysis:** a deterministic TypeScript engine calculates the risk metrics and applies threshold-based rules. It is not a trained ML model.
- **LLM role:** Groq turns the calculated numbers into readable report text and answers chat questions using your holdings. Gemini generates learning content. The LLMs explain results; they don't make the trading decisions.

## Tech Stack

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite, Tailwind CSS, Recharts |
| Backend | Node.js, Express, TypeScript |
| Database | Supabase (PostgreSQL) |
| Auth | JWT, bcrypt, OTP, Google OAuth |
| AI | Groq (Llama 3.3 70B), Google Gemini |
| Market data | Yahoo Finance (`yahoo-finance2`) |
| Email | Brevo |
| Reports | jsPDF |
| Deployment | Render |

## Project Structure

```
Trado/
├── src/          # React frontend
├── backend/
│   └── routes/   # Express feature routers
├── supabase/     # SQL schema and migrations
└── server.ts     # Express server entry point
```

## Getting Started

### Prerequisites
- Node.js 18+
- A Supabase project
- API keys for Groq and Gemini (optional for learning features), plus Brevo for OTP email

### Setup
```bash
npm install
```

1. Create a `.env` file in the project root with your Supabase, JWT, Groq, Gemini and Brevo credentials. Never commit this file.
2. Run the SQL files in `supabase/` in the Supabase SQL Editor to create the tables.
3. Start the app:

```bash
npm run dev
```

## Current Status

**Working:** authentication and onboarding, the virtual trading simulator, Yahoo Finance quotes and charts, risk analytics and recommendations, PDF reports, the Groq chatbot and reports, and Gemini learning content.

**Limitations:**
- The AI report and chat routes need a valid Groq key and have no offline fallback.
- Some portfolio metrics are simplified approximations, not full quantitative models.
- If Yahoo Finance is unavailable, there is no cached fallback.
- There are no automated tests yet.

- **Kamalesh K:** _add your part here_

_Add teammates and their parts here._
