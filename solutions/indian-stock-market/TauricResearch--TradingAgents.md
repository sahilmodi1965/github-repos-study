---
name: "TradingAgents"
repo: "TauricResearch/TradingAgents"
url: "https://github.com/TauricResearch/TradingAgents"
category: "indian-stock-market"
stars: 42900
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-03-28"
production_ready: false
security_score: "Not evaluated"
deploy_complexity: "moderate"
---

## What It Does
Multi-agent LLM trading framework with specialized agents: fundamental analyst, sentiment analyst, technical analyst, trader, and risk manager. Supports OpenAI, Anthropic, Google, xAI, Ollama. Features configurable debate rounds between bullish/bearish researchers before making decisions.

## Use Cases
- **AI-powered stock research:** Multi-agent debate produces balanced buy/sell analysis
- **Sentiment analysis:** Agent that analyzes news and social sentiment per stock
- **Risk management:** Dedicated risk manager agent evaluates position sizing
- **Adaptable for Indian markets:** Plug in Indian data sources (jugaad-data, yfinance .NS) to make it work with NSE/BSE

## Who Uses It in Production
- 42,900 stars — one of the most popular AI trading repos
- Primarily evaluated on US stocks (AAPL, AMZN, GOOGL)
- Requires adaptation for Indian markets

## Tech Stack
- Python, LangChain/LangGraph
- Multi-agent architecture with specialized roles
- Supports: OpenAI, Anthropic, Google, xAI, Ollama
- Default data: Alpha Vantage (US-focused)

## How to Deploy
1. Clone repo, install dependencies
2. Configure LLM API keys
3. **For Indian markets:** Replace Alpha Vantage data source with jugaad-data or yfinance (.NS suffix)
4. Run agents with Indian stock tickers

## Deploy Requirements
- **Min RAM:** 4 GB
- **External deps:** LLM API keys, data source API
- **Estimated cost:** LLM API costs per analysis (~$0.50-2.00 per stock)

## Indian Market Adaptation Needed
- Replace Alpha Vantage with jugaad-data/nsepython/yfinance for NSE data
- No SEBI filing analysis out of the box (no Indian EDGAR equivalent exists)
- Sentiment agent would need Indian news sources (MoneyControl, ET Markets)
- Technical analysis works as-is with OHLCV data from any source

## Limitations & Gotchas
- US-market-centric by default — requires work to adapt for India
- No SEBI/Indian regulatory filing analysis
- Agent debates increase token costs
- Accuracy not independently validated

## Learning Value
- **Architecture patterns:** Multi-agent debate system — bullish vs bearish researchers arguing before a decision
- **Interesting techniques:** Specialized agent roles (fundamental, technical, sentiment, risk) that mirror real trading desks
- **Reusable components:** The agent debate pattern is applicable to any domain needing balanced analysis

## Links
- Repo: https://github.com/TauricResearch/TradingAgents
