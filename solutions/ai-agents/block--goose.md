---
name: "Goose"
repo: "block/goose"
url: "https://github.com/block/goose"
category: "ai-agents"
stars: 42800
license: "Apache-2.0"
language: "Rust"
last_profiled: "2026-04-20"
production_ready: true
security_score: 8
deploy_complexity: "easy"
---

## What It Does
On-machine AI agent that autonomously executes engineering tasks — building projects, running and debugging code, managing workflows, and calling external APIs. Goes beyond code suggestions: it actually runs, tests, and iterates. Works with any LLM provider and integrates with MCP servers for extensibility.

## Use Cases
- Autonomous software prototyping: describe a feature, Goose writes + runs + iterates it
- Codebase refactoring and debugging without manual back-and-forth
- Engineering pipeline automation (build → test → deploy sequences)
- Connecting AI workflows to external APIs and services via MCP
- Teams wanting a self-hosted, provider-agnostic AI dev agent

## Who Uses It in Production
- Built and maintained by Block (formerly Square) — dogfooded internally
- As of April 2026, donated to the **Agentic AI Foundation (AAIF)** at the Linux Foundation — governance now community-driven
- Open-source with active community on Discord and GitHub (4,000+ commits)
- Available as desktop app (Mac/Windows) and CLI; 15+ LLM providers and 70+ extensions supported

## Tech Stack
- Rust (58%) + TypeScript (34%)
- LLM-agnostic: 15+ providers — OpenAI, Anthropic, Google, local models via any compatible API
- MCP (Model Context Protocol) for tool/server extensibility
- Available as CLI and Electron desktop app

## How to Deploy
1. Install via CLI: `curl -fsSL https://github.com/block/goose/releases/latest/download/install.sh | bash`
2. Or download the desktop app from GitHub Releases
3. Configure LLM provider (API key for OpenAI, Anthropic, etc., or local model endpoint)
4. Run `goose session` to start an interactive agent session
5. Optionally: add MCP servers for additional tools (file systems, databases, APIs)

## Deploy Requirements
- **Min RAM:** 512 MB (CLI); 1 GB (desktop app)
- **Min CPU:** Any modern CPU
- **Storage:** ~100 MB for binary + model API calls (no local model required)
- **External deps:** LLM API key (or local model endpoint); MCP servers optional
- **Estimated cost:** $0 self-hosted + LLM API costs (~$5-50/mo depending on usage)

## Security Assessment
- **Scorecard:** ~8/10 (Apache-2.0, maintained by Block/Square)
- **Known CVEs:** None known at time of profiling
- **Signed releases:** Yes (GitHub releases with checksums)
- **Branch protection:** Yes (enforced via Block's GitHub org policies)
- **Dependency pinning:** Yes (Cargo.lock)
- **SBOM available:** Partial via Cargo
- **Notes:** Runs locally with direct filesystem access — scope of agent permissions matters. MCP server trust model requires vetting third-party servers. API keys stored in local config; ensure proper file permissions.

## Limitations & Gotchas
- Agent can make destructive filesystem changes — always use in a project with git
- MCP server quality varies; third-party servers need manual trust assessment
- Long agentic sessions can generate significant LLM API costs
- No built-in sandboxing — agent has same permissions as the running user
- Desktop app is Mac/Windows only; Linux users use CLI

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Cursor | Commercial | IDE-integrated, not agentic-first, less autonomy |
| Claude Code | Commercial CLI | Anthropic-only, tighter integration with Claude |
| Aider | Open Source | Python, code-focused, less general-purpose |
| Cline | Open Source | VS Code extension, similar autonomy but IDE-bound |
| Devin | Commercial | Cloud-hosted, fully managed, $$$  |

## Learning Value
- **Architecture patterns:** How to build a provider-agnostic LLM agent in Rust; tool-calling loop design
- **Interesting techniques:** MCP integration as the extensibility layer — clean separation between agent core and tools
- **Reusable components:** The MCP client implementation; the multi-model provider abstraction

## Links
- Docs: https://block.github.io/goose
- Discord: https://discord.gg/block-goose
- Blog: https://block.github.io/goose/blog
- **Enriched 2026-04-20:** v1.31.1 released; project donated to Linux Foundation AAIF; 42.8K stars (was 37.5K)
