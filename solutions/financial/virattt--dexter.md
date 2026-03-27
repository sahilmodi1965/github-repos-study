---
name: "Dexter"
repo: "virattt/dexter"
url: "https://github.com/virattt/dexter"
category: "financial"
stars: 19636
license: "MIT"
language: "TypeScript"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "moderate"
---

## What It Does
Autonomous AI agent for deep financial research. Takes complex questions ("find undervalued semiconductor stocks"), decomposes them into research plans, executes using real-time market data and SEC filings, self-validates through iterative refinement, and produces data-backed investment analyses. Described as "Claude Code, but for finance."

## Use Cases
- Equity research: stock screening, fundamental analysis
- SEC filing review (10-K, 10-Q, 8-K analysis)
- Investment thesis generation with data backing
- Competitive landscape analysis for industries
- Individual investors wanting institutional-grade research without Bloomberg/FactSet costs

## Who Uses It in Production
- 19K+ stars, strong adoption among retail investors and financial analysts
- WhatsApp gateway for conversational access

## Tech Stack
- TypeScript, Bun runtime, LangChain.js
- **4-agent architecture:** Planning Agent → Action Agent → Validation Agent → Answer Agent
- Financial Datasets API (institutional-grade: income statements, balance sheets, cash flow). Free tier covers AAPL, NVDA, MSFT only.
- SEC filing reader (10-K, 10-Q, 8-K)
- Exa API (preferred) or Tavily API (fallback) for web search
- Playwright-based web scraping for discovered pages
- Supports: OpenAI, Anthropic, Google, xAI, OpenRouter, Ollama (local)
- Evaluation: LangSmith with LLM-as-judge scoring

## How to Deploy
1. Clone repo, install with Bun
2. Configure LLM provider (cloud API or local Ollama)
3. Set up Financial Datasets API key
4. Run CLI or connect WhatsApp gateway

## Deploy Requirements
- **Min RAM:** 2-4 GB
- **Min CPU:** 2 cores
- **External deps:** Financial Datasets API key, LLM API key (or Ollama)
- **Estimated cost:** Free tool + API costs. Financial Datasets API has free tier. LLM costs vary.

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** Yes (2 workflows)
- **Signed releases:** No (3 releases, no assets)
- **Contributors:** ~17
- **Last commit:** 2026-03-26
- **Open issues:** 62
- **Code of Conduct:** None
- **Dependency pinning:** Yes (package-lock.json + bun.lock)
- **Notes:** Handles financial data — ensure API keys are secured. No branch protection is a concern for a financial tool.

## Community Sentiment
- **Low independent validation:** Two HN submissions (Dec 2025, Feb 2026) each got 1 point and 0 comments
- No Reddit discussions found — most coverage is from Medium blog posts and creator's Twitter
- **Honest assessment:** More of a well-designed proof-of-concept than a production-tested tool
- No published accuracy percentages or benchmarks exist

## Limitations & Gotchas
- Financial advice disclaimer: outputs are research, not investment recommendations
- **Financial Datasets API free tier only covers AAPL, NVDA, MSFT** — paid plan needed for broader coverage
- Data quality depends on Financial Datasets API coverage
- Self-validation adds latency — deep research takes minutes
- Loop detection and execution limits are safety mechanisms, not bugs
- No published accuracy benchmarks — "you should still verify critical findings against source data"

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Bloomberg Terminal | Commercial ($$$) | Gold standard but $24K/year |
| AlphaVantage + LLM | DIY | Cheaper data, no agentic loop |
| FinGPT | Open Source | More focused on model fine-tuning than agentic research |
| Composer | Commercial | Automated trading, less research-focused |

## Learning Value
- **Architecture patterns:** Agentic loop with task planning, tool selection, execution, and self-reflection
- **Interesting techniques:** Self-validation loop for trust in financial outputs, LLM-as-judge evaluation
- **Reusable components:** The agentic research loop pattern (plan → execute → validate → refine) is applicable to any domain

## Links
- Repo: https://github.com/virattt/dexter
- Analysis: https://yuv.ai/blog/dexter
