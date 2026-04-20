---
name: "Codex CLI"
repo: "openai/codex"
url: "https://github.com/openai/codex"
category: "ai-agents"
stars: 76500
license: "Apache-2.0"
language: "Rust"
last_profiled: "2026-04-20"
production_ready: true
security_score: 8
deploy_complexity: "trivial"
---

## What It Does
Lightweight terminal-native coding agent from OpenAI that reads your codebase, writes and edits code, runs shell commands, and iterates on errors — all in one sandboxed loop. Built in Rust for speed, it integrates with ChatGPT plans or any OpenAI-compatible API key and supports IDE extensions for VS Code, Cursor, and Windsurf.

## Use Cases
- Autonomous coding tasks directly from the terminal without leaving the shell
- Codebase exploration and refactoring with agentic multi-file edits
- CI/CD scripting: run codex as a non-interactive step in pipelines
- Pair-programming in the terminal for developers who prefer CLI over IDE
- Teams wanting an OpenAI-backed alternative to Claude Code or Goose

## Who Uses It in Production
- Maintained by OpenAI — dogfooded across internal teams
- Available to ChatGPT Plus/Pro/Business/Edu/Enterprise subscribers
- 718 releases as of April 2026; 76K+ community adopters

## Tech Stack
- Rust (95%) — core agent loop and sandboxed execution
- Python (2.5%) + TypeScript (1.3%) — scripting helpers
- OpenAI API (default); supports any OpenAI-compatible endpoint
- Install via npm (`@openai/codex`), Homebrew, or binary download

## How to Deploy
1. `npm install -g @openai/codex` or `brew install --cask codex`
2. Set `OPENAI_API_KEY` in your environment (or sign in via ChatGPT account)
3. Run `codex` in any project directory
4. Optional: install VS Code / Cursor / Windsurf extension for IDE integration
5. For CI use: run `codex --non-interactive "<task>"` in pipeline steps

## Deploy Requirements
- **Min RAM:** 256 MB
- **Min CPU:** Any modern CPU (Rust binary, very lightweight)
- **Storage:** ~50 MB binary + project files
- **External deps:** OpenAI API key or ChatGPT Plus subscription
- **Estimated cost:** $0 binary; LLM API costs ~$5–30/mo depending on usage

## Security Assessment
- **Scorecard:** ~8/10 (Apache-2.0, OpenAI org, SECURITY.md present)
- **Known CVEs:** None as of 2026-04-20
- **Signed releases:** Yes (GitHub Releases with platform binaries + checksums)
- **Branch protection:** Yes (OpenAI org enforces review)
- **Dependency pinning:** Yes (Cargo.lock)
- **SBOM available:** Not published separately
- **Notes:** Sandboxed execution model limits blast radius of agent actions. API keys stored in env vars — use secrets manager in CI. The cloud Codex Web version has additional OpenAI data handling terms.

## Limitations & Gotchas
- Primarily optimized for OpenAI models; other providers need compatibility shim
- Non-interactive CI mode is powerful but requires careful prompt scoping
- No built-in multi-agent orchestration — single agent loop only
- Desktop/IDE integrations are secondary to the terminal-first experience
- Codex Web (cloud) is a different product with different pricing and privacy terms

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Claude Code | Commercial CLI | Anthropic-only, tighter editor integration |
| block/goose | Open Source | LLM-agnostic, MCP-extensible, Linux Foundation |
| Aider | Open Source | Python, model-agnostic, mature RAG features |
| Cline | Open Source | VS Code extension, strong UI for reviewing changes |
| Devin | Commercial | Cloud-hosted, fully autonomous, $$$  |

## Learning Value
- **Architecture patterns:** Rust-based agent loop with sandboxed shell execution — reference for building safe autonomous agents
- **Interesting techniques:** Non-interactive mode enables agentic CI steps; API compatibility layer makes it provider-swappable
- **Reusable components:** The sandboxed execution wrapper; the multi-platform binary distribution pipeline

## Links
- Docs: https://github.com/openai/codex#readme
- Releases: https://github.com/openai/codex/releases
- Blog: https://openai.com/codex/
