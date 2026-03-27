---
name: "OpenAlgo"
repo: "marketcalls/openalgo"
url: "https://github.com/marketcalls/openalgo"
category: "indian-stock-market"
stars: 1600
license: "AGPL-3.0"
language: "Python"
last_profiled: "2026-03-28"
production_ready: true
security_score: "Not evaluated"
deploy_complexity: "moderate"
---

## What It Does
Self-hosted algorithmic trading platform that unifies 30+ Indian brokers behind a single REST API. Includes visual strategy builder (drag-and-drop), Python strategy manager, MCP server for AI integration, Telegram bot, and an API analyzer with virtual Rs 1 Crore capital for paper trading.

## Use Cases
- **Unified broker access:** Single API for Zerodha, Angel One, Upstox, Groww, Dhan, Fyers, 5paisa, AliceBlue, Kotak Neo, IIFL, Motilal Oswal, Samco, and 18+ more
- **Algo trading:** Build and deploy automated strategies across any Indian broker
- **AI-powered trading:** MCP server integration for connecting AI agents to live markets
- **Paper trading:** Test strategies with virtual Rs 1 Cr capital before going live
- **Strategy building:** Visual drag-and-drop builder for non-coders

## Who Uses It in Production
- 1,600+ stars, actively maintained (2026)
- From the same developer (marketcalls) as OpenChart
- Indian Algorithmic Trading Community adoption

## Tech Stack
- Python (Flask) + JavaScript/React
- REST API architecture
- Supports 30+ Indian broker APIs behind unified interface
- MCP server for AI agent integration
- Telegram bot for notifications/control
- Self-hosted (Docker or direct)

## How to Deploy
1. Clone repo, install Python dependencies
2. Configure broker credentials (API keys from your broker)
3. Run Flask server
4. Access web UI for strategy building and monitoring

## Deploy Requirements
- **Min RAM:** 2-4 GB
- **Min CPU:** 2 cores
- **External deps:** Broker account with API access (e.g., Zerodha Kite Connect Rs 2,000/mo)
- **Estimated cost:** Free tool + broker API subscription

## Security Assessment
- **Notes:** Handles live trading credentials — deploy on private infrastructure only. AGPL license requires sharing modifications if deployed as a service.

## Limitations & Gotchas
- AGPL license — copyleft, must open-source modifications if you deploy as a service
- Each broker integration has its own quirks and rate limits
- Requires paid broker API subscription (Kite Connect Rs 2,000/mo, others vary)
- Self-hosted only — you manage infrastructure and uptime

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Zerodha Streak | Commercial | Easier but limited to Zerodha, paid |
| Tradetron | Commercial | Multi-broker but subscription-based |
| Fenix | Open Source | Similar concept but unmaintained (last commit Apr 2024) |

## Learning Value
- **Architecture patterns:** Multi-broker abstraction layer — how to unify disparate APIs
- **Interesting techniques:** MCP server for AI agent → live market bridge
- **Reusable components:** The broker adapter pattern is applicable to any multi-provider system

## Links
- Repo: https://github.com/marketcalls/openalgo
