# Weekly Discovery Digest — 2026-04-06

## Summary
Active discovery week. GitHub trending showed strong growth in AI agent frameworks and developer tooling. Three new profiles created, five new watchlist entries added (one updated), and two existing profiles enriched with updated star counts and release data.

---

## New Profiles Created (3)

### 1. `block/goose` → `solutions/ai-agents/block--goose.md`
- **Stars:** 37.5K | **License:** Apache-2.0 | **Language:** Rust + TypeScript
- **Why:** On-machine autonomous AI agent from Block (Square). Provider-agnostic, MCP-extensible, latest release v1.29.1 (2026-04-03). Strong production story with enterprise backing.
- **Category:** ai-agents

### 2. `roboflow/supervision` → `solutions/computer-vision/roboflow--supervision.md`
- **Stars:** 37.7K | **License:** MIT | **Language:** Python
- **Why:** The de-facto standard post-processing toolkit for computer vision pipelines. Model-agnostic, works with YOLO/SAM/Transformers, active commits on 2026-04-06. High business relevance for surveillance, retail, sports analytics.
- **Category:** computer-vision

### 3. `siddharthvaddem/openscreen` → `solutions/dev-tools/siddharthvaddem--openscreen.md`
- **Stars:** 23.2K | **License:** MIT | **Language:** TypeScript
- **Why:** Viral this week (+12.7K stars in 7 days). Free Screen Studio alternative — product demo and screencast tool with cinematic effects. Useful for SaaS marketing teams and developer content. Latest v1.3.0 (2026-04-02).
- **Category:** dev-tools
- **Watch:** Solo maintainer — monitor for abandonment

---

## Watchlist Updates (5 new, 1 updated)

| Repo | Stars | Note |
|------|-------|------|
| sherlock-project/sherlock | ~79.9K | OSINT username hunter across 400+ networks — high stars, production security use |
| google-research/timesfm | ~15K | Google's time-series foundation model for zero-shot forecasting — financial/IoT applicability |
| badlogic/pi-mono | ~32.1K | AI agent toolkit (CLI + unified LLM API + TUI) — trending this week |
| vas3k/TaxHacker | ~4.7K | Self-hosted AI accounting app — below 5K stars threshold but strong concept |
| NousResearch/hermes-agent | ~26.97K | **Updated** — was 19.9K on 2026-03-31; now at 26.97K (+7K stars in one week) |

---

## Profiles Enriched (2)

### `n8n-io/n8n`
- Stars: 105K → **183K** (major growth — nearly doubled)
- Latest release: v2.14.2 (2026-03-26)
- New: 900+ pre-built workflow templates now available

### `twentyhq/twenty`
- Stars: 41.9K → **43.6K**
- Latest release: v1.20.0 (2026-03-31) — active shipping cadence confirmed

---

## Notable Trends

1. **AI agent tooling fracturing by runtime** — Goose (Rust, on-machine), pi-mono (TypeScript, CLI+TUI), and Hermes (Python) each targeting different developer profiles.
2. **Computer vision productization** — Supervision's 37.7K stars signals the CV pipeline tooling layer is a real product surface.
3. **n8n's explosive growth** — 105K → 183K stars; likely a viral event. Worth tracking conversion to new deployments.
4. **Demo/content tooling going open-source** — OpenScreen's viral week (+12.7K stars) signals strong Loom/Screen Studio pricing pain.
5. **Sherlock (79.9K) was overlooked** — Mature OSINT tool with very high stars not previously tracked; security tooling deserves more coverage.

---

## Repos Skipped This Week
- `luongnv89/claude-howto` — Educational guide, not a deployable solution
- `asgeirtj/system_prompts_leaks` — Not a production tool
- `Blaizzy/mlx-vlm` — Only 4K stars, below threshold
- `google-ai-edge/gallery` — Kotlin showcase app, not a deployable backend

## Errors / Issues
- HN Algolia API returned 403 again — sourced via web search instead
- Several web pages returned 403 (shareuhack.com, bytebytego.com, dev.to) — GitHub trending page fetched directly as fallback

---

# Weekly Discovery Digest — 2026-03-31

## Summary
- **New profiles created:** 3
- **Added to watchlist:** 13 new entries
- **Profiles enriched:** 2
- **Searches run:** 3 (GitHub trending, HN Show HN, production-ready tools 2026)

---

## New Profiles Created

| Profile | Category | Stars | Why Profiled |
|---------|----------|-------|-------------|
| `karpathy/autoresearch` | ai-research | ~53,500 | Karpathy's autonomous ML research agent; single-GPU loop; high community trust |
| `n8n-io/n8n` | workflow-automation | ~105,000 | #1 self-hostable workflow automation; 400+ integrations; native AI nodes |
| `PaddlePaddle/PaddleOCR` | ai-ocr | ~73,982 | 100+ language OCR with PDF/table extraction; Apache-2.0; production-proven |

---

## Profiles Enriched

| Profile | Change |
|---------|--------|
| `obra/superpowers` | Stars updated: 118,339 → 127,000 (+8,661 since 2026-03-28); still #1 Claude Code plugin |
| `microsoft/VibeVoice` | Stars updated: 24,625 → 32,713 (+8,088 since 2026-03-28); rapid growth continues |

---

## Added to Watchlist (13 new entries)

| Repo | Category | Notes |
|------|----------|-------|
| `onlook-dev/onlook` | frontend-tools | ~21.6K stars; visual React editor; Show HN 100+ pts |
| `NousResearch/hermes-agent` | ai-agents | ~19.9K stars; general-purpose agent framework |
| `ollama/ollama` | llm-inference | ~100K+ stars; local LLM inference; production-grade |
| `open-webui/open-webui` | ai-ui | ~60K+ stars; polished UI for Ollama + LLMs |
| `biomejs/biome` | dev-tools | ~20K+ stars; Rust linter+formatter, 100x faster than ESLint |
| `continuedev/continue` | dev-tools | ~25K+ stars; open AI coding assistant, LLM-agnostic |
| `plane-so/plane` | project-management | ~30K+ stars; self-hostable Jira/Linear alternative |
| `promptfoo/promptfoo` | ai-testing | ~6K+ stars; LLM red-teaming + evaluation toolkit |
| `smart-mcp-proxy/mcpproxy-go` | mcp-tooling | MCP server federation; quarantines malicious servers |
| `aditya-nadkarni/spongecake` | ai-agents | Computer-use SDK for OpenAI agents on virtual desktops |
| `gitleaks/betterleaks` | security | Next-gen secrets scanner with 98.6% recall |
| `yohannesgk/blacksmith` | security | Multi-agent AI penetration testing framework |

---

## Notable Trends This Week

1. **AI agent harnesses exploding** — `obra/superpowers` gained 8K+ stars in 3 days; ecosystem around Claude Code / Codex / Gemini CLI is maturing fast. The "agent configuration layer" is becoming a real product category.

2. **Local LLM inference going mainstream** — `ollama/ollama` at 100K+ stars, `open-webui` at 60K+. The stack for private, self-hosted AI is now nearly plug-and-play. This removes a major barrier for enterprise privacy requirements.

3. **MCP ecosystem tooling emerging** — `smart-mcp-proxy/mcpproxy-go` and similar tools signal that Model Context Protocol is generating its own tooling ecosystem (similar to how npm grew around Node). Worth watching for security implications.

4. **AI-native security tools** — `yohannesgk/blacksmith` (AI pentesting) and `gitleaks/betterleaks` (ML-based secrets detection) indicate that offensive and defensive security are both getting AI-native rebuilds in 2026.

5. **Autonomous research loops** — `karpathy/autoresearch` (53K stars) and `SakanaAI/AI-Scientist-v2` (already in brain) both show the "AI doing science" paradigm is gaining real traction and community trust.

---

## Skipped / Not Relevant

- `affaan-m/everything-claude-code` — already tracked as competitor in obra/superpowers profile
- `Yeachan-Heo/oh-my-claudecode` — already in solutions/
- `microsoft/VibeVoice` — already in solutions/ (enriched above)
- `obra/superpowers` — already in solutions/ (enriched above)
- `sherlock-project/sherlock` — OSINT tool; 75K stars but not in core focus areas
- `neovim/neovim` — editor, not a deployable solution
- `jwasham/coding-interview-university` — educational, not a tool
- `withastro/astro` / `oven-sh/bun` — web framework / runtime; outside brain's focus on AI/infra solutions
- `argoproj/argo-cd` / `localstack/localstack` — DevOps infra; valid but deprioritized this run

---

## Errors / Issues
- HN Algolia API (`hn.algolia.com`) returned 403 — domain not reachable from agent sandbox. HN data sourced via web search instead.
- Star counts for several watchlist entries (`smart-mcp-proxy/mcpproxy-go`, `spongecake`, `betterleaks`, `blacksmith`) could not be confirmed from search results — marked as "~unknown". Should verify before profiling.
