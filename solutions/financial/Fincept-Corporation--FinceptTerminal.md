---
name: "FinceptTerminal"
repo: "Fincept-Corporation/FinceptTerminal"
url: "https://github.com/Fincept-Corporation/FinceptTerminal"
category: "financial"
stars: 15900
license: "AGPL-3.0"
language: "Python"
last_profiled: "2026-04-27"
production_ready: true
security_score: 6
deploy_complexity: "easy"
---

## What It Does
Open-source Bloomberg-terminal alternative built with C++20/Qt6 UI and embedded Python analytics. Delivers institutional-grade financial intelligence: equity research, portfolio optimization, real-time trading, and quantitative analysis — all on your own machine. Ships 37 AI trading agents modeled after famous investors (Buffett, Graham, Lynch) plus macroeconomic and geopolitical frameworks.

## Use Cases
- Individual investors wanting Bloomberg-class analytics without the $20K/yr subscription
- Quant researchers: DCF models, VaR/Sharpe metrics, QuantLib suite (18 modules)
- Real-time trading: crypto + equity with paper trading engine for strategy testing
- Portfolio management: optimization, risk metrics, multi-broker integration
- Financial educators building interactive curriculum with live market data

## Who Uses It in Production
- 15.9K stars with strong weekly growth (10K new stars week of April 20, 2026)
- v4.0.2 released April 24, 2026 — actively maintained with 26 releases
- Designed for individual traders and quant analysts; not enterprise-IT-deployed
- Dual-licensed: AGPL-3.0 (open) + commercial license for proprietary use

## Tech Stack
- C++20 (39.6%) + Python (59.8%)
- Qt6 for the desktop UI
- 100+ data connectors: Yahoo Finance, FRED, IMF, World Bank, Polygon, Kraken
- 16 broker integrations
- QuantLib for derivatives pricing and quant analysis
- Embedded Python for analytics; node editor for visual workflow automation

## How to Deploy
1. **Recommended:** Download pre-built installer for Windows/Linux/macOS from GitHub Releases
2. **Self-build (Linux/macOS):** `git clone … && ./setup.sh` (auto-handles deps)
3. **Docker:** available for CI/CD environments (requires X11 on Linux)
4. **Manual build:** CMake presets with Qt 6.8.3, Python 3.11.9, C++20 compiler

## Deploy Requirements
- **Min RAM:** 4 GB (8 GB recommended for heavy analytics)
- **Min CPU:** Any modern multi-core (x86_64 or ARM64)
- **Storage:** 2 GB for app + cache space for historical data
- **External deps:** Internet access for live data feeds; some connectors need API keys (Polygon, Kraken, etc.)
- **Estimated cost:** Free (AGPL) + data API costs; many connectors use free-tier Yahoo Finance/FRED

## Security Assessment
- **Scorecard:** ~6/10 (newer project; AGPL-3.0; active releases)
- **Known CVEs:** None at time of profiling; project is relatively young
- **Signed releases:** GitHub Releases with checksums
- **Branch protection:** Standard GitHub protections
- **Dependency pinning:** CMake presets pin Qt/Python versions (good practice)
- **SBOM available:** No
- **Notes:** AGPL-3.0 means any modifications must be open-sourced — check before embedding in commercial products. API keys stored locally; review storage location for your OS. No server component — pure desktop app, lower attack surface.

## Limitations & Gotchas
- AGPL-3.0 license: if you modify and distribute, you must open-source your changes
- C++/Qt6 build from source is non-trivial without the installer script
- Real-time data quality depends on the free data connectors — Yahoo Finance can be rate-limited
- AI trading agents are for research/simulation, not autonomous live trading decisions
- Docker mode requires X11 — headless server deployments need VNC/XVnc workaround
- Newer project (rapid star growth may reflect hype); evaluate stability for production use

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| OpenBB Platform | Open Source | Python-native, more library/API-first, less UI |
| Virattt/dexter | Open Source | Simpler AI-only research agent, no trading engine |
| Bloomberg Terminal | Commercial ($20K/yr) | Gold standard data quality, zero self-hosting |
| TradingView | Commercial | Cloud-only, strong charting, limited data export |
| Qlib (Microsoft) | Open Source | Research framework, not a terminal UI |

## Learning Value
- **Architecture patterns:** Embedding Python analytics engine inside a C++ desktop application; Qt6 signal/slot model for live data updates
- **Interesting techniques:** Node editor for visual quant workflow building — re-engineering this pattern for other analytics domains
- **Reusable components:** The multi-broker API abstraction layer; the QuantLib integration wrapper

## Links
- Docs: https://github.com/Fincept-Corporation/FinceptTerminal/wiki
- Discord: https://discord.gg/fincept
- Releases: https://github.com/Fincept-Corporation/FinceptTerminal/releases
