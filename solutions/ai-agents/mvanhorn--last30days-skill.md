---
name: "last30days-skill"
repo: "mvanhorn/last30days-skill"
url: "https://github.com/mvanhorn/last30days-skill"
category: "ai-agents"
stars: 12477
license: "MIT"
language: "Python"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "easy"
---

## What It Does
AI agent skill that researches any topic across 10 platforms (Reddit, X, Bluesky, Truth Social, YouTube, TikTok, Instagram, Hacker News, Polymarket, web search) from the past 30 days. Scores, deduplicates, and synthesizes results into a grounded narrative with real citations. Research takes 2-8 minutes.

## Use Cases
- Real-time market/sentiment research: "what are people saying about {product}?"
- Competitive intelligence across social platforms
- Trend tracking and early signal detection
- Product launch monitoring
- Prediction market signal (Polymarket integration)
- Due diligence on technologies or companies

## Who Uses It in Production
- Part of the Claude Code skills ecosystem
- 12K+ stars indicates broad adoption among AI agent users

## Tech Stack
- Python skill files
- Multi-pass query expansion with parallel search
- APIs: ScrapeCreators (Reddit/TikTok/Instagram), AT Protocol (Bluesky), Brave/Perplexity (web)
- Polymarket: 5-factor weighted ranking (relevance 30%, volume 30%, liquidity 15%, price velocity 15%, outcome competitiveness 10%)
- Composite scoring: text similarity, engagement velocity, temporal recency, source authority

## Required API Keys
| API Key | Source Covered | Required? |
|---------|---------------|-----------|
| `SCRAPECREATORS_API_KEY` | Reddit, TikTok, Instagram | Primary (100 free credits, then pay-as-you-go) |
| `AUTH_TOKEN` + `CT0` | X/Twitter (cookies) | Recommended for X |
| `XAI_API_KEY` | X fallback | Optional ($0.20/M input tokens) |
| `BSKY_HANDLE` + `BSKY_APP_PASSWORD` | Bluesky | Optional |
| `PARALLEL_API_KEY` / `BRAVE_API_KEY` | Web search | Optional |

Three modes: reddit-only, x-only, or both (full cross-validation).

## How to Deploy
1. `git clone` into Claude Code skills directory
2. Configure API keys for search providers (see table above)
3. Invoke via Claude Code
4. Briefings auto-save to `~/Documents/Last30Days/`

## Deploy Requirements
- **Min RAM:** N/A (runs within agent)
- **External deps:** API keys — minimum ScrapeCreators for Reddit, add more for broader coverage
- **Estimated cost:** Free skill + a few cents to low single-digit dollars per query depending on config
- **Quality:** Blinded evaluation scored **4.38/5.0** (vs 3.73 for v1) across 5 test topics

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** None (0 workflows)
- **Signed releases:** No
- **Contributors:** ~8
- **Last commit:** 2026-03-24
- **Open issues:** 48
- **Code of Conduct:** None
- **Dependency pinning:** No lockfile
- **Security posture: LOW** — no CI, no branch protection, no lockfile. Acceptable for a skill project but review code before trusting with API keys.

## Limitations & Gotchas
- Requires multiple API keys for full coverage
- Research takes 2-8 minutes (not instant)
- Quality depends on API availability and rate limits
- Social platform APIs can change/break

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Perplexity | Commercial | Web-only, no social platform depth |
| Grok (xAI) | Commercial | X-focused, limited cross-platform |
| Tavily | API | Web search API, no social aggregation |
| Custom MCP servers | DIY | Build your own per-platform connectors |

## Learning Value
- **Architecture patterns:** Multi-source aggregation with composite scoring
- **Interesting techniques:** Polymarket signal integration, engagement velocity scoring, two-phase supplemental search
- **Reusable components:** The multi-platform search + dedup + scoring pipeline pattern

## Links
- Repo: https://github.com/mvanhorn/last30days-skill
