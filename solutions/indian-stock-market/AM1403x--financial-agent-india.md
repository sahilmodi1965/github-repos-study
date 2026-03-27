---
name: "financial-agent-india"
repo: "AM1403x/financial-agent-india"
url: "https://github.com/AM1403x/financial-agent-india"
category: "indian-stock-market"
stars: 99
license: "MIT"
language: "Python"
last_profiled: "2026-03-28"
production_ready: false
security_score: "Not evaluated"
deploy_complexity: "easy"
---

## What It Does
AI-powered financial analysis agent built specifically for Indian stock markets. Uses AngelOne SmartAPI for live NSE/BSE data + Claude for analysis. Supports live quotes, historical OHLCV candles, options chain with Greeks/IV, WebSocket real-time streaming, and order placement (dry-run by default).

## Use Cases
- **Indian stock analysis:** AI-powered technical analysis on NSE/BSE stocks
- **Options analysis:** Options chain with Greeks and implied volatility
- **Real-time monitoring:** WebSocket streaming for live market data
- **Paper trading:** Dry-run order placement by default

## Who Uses It in Production
- Small project (~99 stars), early stage
- **The only purpose-built AI agent specifically for Indian markets**
- Default stocks: RELIANCE, TCS, INFY, HDFCBANK

## Tech Stack
- Python + Claude API
- AngelOne SmartAPI for market data
- WebSocket for real-time streaming
- Default focus on Nifty 50 stocks

## How to Deploy
1. Install Python dependencies
2. Get AngelOne account + API credentials
3. Get Claude API key
4. Configure and run

## Deploy Requirements
- **Min RAM:** 2 GB
- **External deps:** AngelOne account, Claude API key
- **Estimated cost:** Claude API costs per analysis session

## Limitations & Gotchas
- **Very early stage** — only 99 stars, small community
- Locked to AngelOne broker (no multi-broker support)
- No fundamental analysis (no financial statements, balance sheets)
- No SEBI filing analysis
- Requires AngelOne account specifically

## Why It Matters
This is the ONLY open-source AI agent built specifically for Indian markets. While small, it proves the concept. Could be combined with jugaad-data + OpenAlgo for a more complete solution.

## Links
- Repo: https://github.com/AM1403x/financial-agent-india
