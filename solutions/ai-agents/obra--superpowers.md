---
name: "Superpowers"
repo: "obra/superpowers"
url: "https://github.com/obra/superpowers"
category: "ai-agents"
stars: 118339
license: "MIT"
language: "Shell"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB (skill files, not compiled software)"
deploy_complexity: "trivial"
---

## What It Does
An agentic skills framework that forces AI coding agents through a disciplined engineering pipeline: brainstorming, design validation, detailed planning, subagent-driven implementation with TDD, code review, and branch completion. Turns "vibe coding" into repeatable, tested, reviewable software engineering.

## Use Cases
- Enforce engineering methodology on AI-generated code (requirements → design → TDD → review)
- Manage complex multi-file refactors with subagent parallelism
- Teams wanting consistent AI coding quality across developers
- Any project where AI-written code needs to be production-grade, not prototype-grade

## Who Uses It in Production
- Launched same day as Anthropic's Claude Code plugin system (Oct 2025)
- #1 Claude Code plugin by stars
- Widely adopted across the Claude Code, Cursor, Codex, and Gemini CLI ecosystems
- Created by Jesse Vincent (obra), well-known open-source maintainer

## Tech Stack
- Shell scripts + structured markdown skill files
- Works across 11+ tools: Claude Code, Codex CLI, Gemini CLI, Cursor, Aider, Windsurf, etc.
- Uses the Agent Skills open standard (SKILL.md format)

## How to Deploy
1. `git clone https://github.com/obra/superpowers.git ~/.claude/skills/superpowers`
2. Or install via Claude Code plugin marketplace
3. Skills are automatically loaded by compatible agents

## Deploy Requirements
- **Min RAM:** N/A (it's prompts, not infrastructure)
- **Min CPU:** N/A
- **Storage:** ~10MB
- **External deps:** A compatible AI coding agent (Claude Code, Cursor, etc.)
- **Estimated cost:** Free (you pay for the underlying LLM API calls)

## Security Assessment
- **Scorecard:** TODO
- **Known CVEs:** None reported
- **Signed releases:** N/A (skill files, not compiled software)
- **Branch protection:** Yes
- **Dependency pinning:** N/A
- **SBOM available:** N/A
- **Notes:** Minimal attack surface — it's structured prompts, not executable code. The main risk is prompt injection if skills are modified by untrusted sources.

## Community Sentiment
- **Positive:** "took my Claude Code experience from mostly frustrating to nearly-magical" (HN, Feb 2026)
- **Positive:** "works surprisingly well for Claude... in the context of rather small side projects in Elixir" (HN, Nov 2025)
- **Mixed:** Agents using superpowers are "completely siloed" with no shared context between different LLM agents (HN, Mar 2026)
- **Mixed:** Difficulty knowing whether superpowers is actually being invoked — "I can't really know if it's doing anything different than standard plan mode" (GitHub #446)

## Known Issues
- **Token bloat** (GitHub #512): Generated plans can be 48K chars (~12-15K tokens); by Task 3-4, auto-context-compression kicks in, costing another 12-15K tokens per re-read cycle
- **Skill skipping** (GitHub #528): Claude sometimes skips spec and code quality review "because it wanted to go faster," breaking the enforced workflow
- **Opacity** (GitHub #446): Hard to verify the skills are actually active

## Limitations & Gotchas
- Increases token usage significantly (multi-phase pipeline = more LLM calls)
- Opinionated methodology — may conflict with teams that have their own process
- TDD enforcement can slow down prototyping when you just want quick experiments
- Subagent spawning requires Claude Code or similar agent with subagent support
- **Only truly effective on small-to-medium side projects** — large monorepo brownfield projects remain challenging
- The "1% Rule" (if there's even a 1% chance a skill applies, invoke it) can be overzealous

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| oh-my-claudecode | Open Source | Multi-agent orchestration focus, 32 parallel agents |
| everything-claude-code | Open Source | 112K stars, ships 28 agents + 119 skills (broader but less opinionated) |
| Cursor Rules | Built-in | Simpler, single-agent, no enforced methodology |
| Aider conventions | Open Source | Lighter weight, focused on git integration |

## Learning Value
- **Architecture patterns:** How to structure a multi-phase agent pipeline with mandatory gates
- **Interesting techniques:** Enforced TDD (RED-GREEN-REFACTOR with automatic deletion of code written before tests), two-stage subagent review
- **Reusable components:** The skill file format itself — portable across 11+ tools via Agent Skills spec

## Links
- Docs: https://github.com/obra/superpowers/blob/main/README.md
- Blog: https://blog.fsck.com/2025/10/09/superpowers/
- Analysis: https://emelia.io/hub/superpowers-claude-code-framework
