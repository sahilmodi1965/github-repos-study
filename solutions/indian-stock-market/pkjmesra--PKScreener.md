---
name: "PKScreener"
repo: "pkjmesra/PKScreener"
url: "https://github.com/pkjmesra/PKScreener"
category: "indian-stock-market"
stars: 325
license: "Available"
language: "Python"
last_profiled: "2026-03-28"
production_ready: true
security_score: "Not evaluated"
deploy_complexity: "easy"
---

## What It Does
India's most feature-rich open-source stock screener for NSE. 40+ built-in scanners, technical indicators (RSI, MACD, CCI, ATR), AI-powered Nifty prediction for gap-up/gap-down, Telegram bot integration, backtesting, and multi-platform support (Windows, macOS, Linux, Docker).

## Use Cases
- **Daily stock screening:** 40+ scanners for breakout, momentum, volume, pattern detection
- **Nifty prediction:** AI model predicting gap-up/gap-down
- **Swing trading signals:** Identify stocks with breakout probability
- **Automated alerts:** Telegram bot for real-time notifications
- **Backtesting:** Test screening criteria against historical data

## Who Uses It in Production
- 325 stars, actively maintained (v0.46, Mar 2026)
- Covers Nifty 50/100/200/500/Midcap/Smallcap universes

## Tech Stack
- Python, TA-Lib (optional), pandas
- Telegram bot integration
- Docker support
- Cross-platform (Windows, macOS, Linux)

## How to Deploy
1. `pip install PKScreener` or Docker
2. Download OHLC data (built-in command)
3. Run screener with desired scan type
4. Optional: configure Telegram bot for alerts

## Deploy Requirements
- **Min RAM:** 2 GB
- **Min CPU:** Any
- **External deps:** TA-Lib (optional, platform-specific install)
- **Estimated cost:** Free

## Limitations & Gotchas
- TA-Lib installation can be tricky (requires C library)
- OHLC data must be downloaded before scanning (not real-time)
- Scheduled alerts only during NSE trading hours
- Technical analysis only — no fundamental screening (use Screener.in for that)

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Screeni-py | Open Source (675 stars) | Similar, MIT license, Docker GUI |
| Screener.in | Commercial | Fundamentals-focused, no API |
| Tickertape | Commercial | More polished, paid premium |
| Chartink | Commercial | Real-time, subscription-based |

## Links
- Repo: https://github.com/pkjmesra/PKScreener
