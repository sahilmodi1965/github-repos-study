---
name: "oh-my-claudecode"
repo: "Yeachan-Heo/oh-my-claudecode"
url: "https://github.com/Yeachan-Heo/oh-my-claudecode"
category: "ai-agents"
stars: 13856
license: "MIT"
language: "TypeScript"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "easy"
---

## What It Does
Multi-agent orchestration layer for Claude Code. Coordinates up to 32 specialized AI agents across a staged pipeline (planning → design → execution → verification → fix loops). Spawns parallel Claude instances in real tmux sessions, auto-routes between cheap models (Haiku) for simple tasks and expensive models (Opus) for complex reasoning.

## Use Cases
- Speed up complex coding tasks 3-5x via parallel agent execution
- Cost optimization — 30-50% token savings through smart model routing
- Teams wanting coordinated multi-agent development workflows
- Large refactors, migrations, or feature builds that span many files

## Who Uses It in Production
- Growing adoption in Claude Code power-user community
- 13K+ stars in short time indicates strong developer interest

## Tech Stack
- TypeScript, tmux for real worker processes
- Smart model routing (Haiku vs Opus based on task complexity)
- 32 domain-specialized agents (architecture, research, design, testing, data science)
- Persistent state in `.omc/` directories
- MCP integration points

## How to Deploy
1. Install via npm/plugin marketplace
2. Requires tmux installed on system
3. Configure model preferences and agent count

## Deploy Requirements
- **Min RAM:** Depends on number of parallel agents
- **Min CPU:** Multi-core recommended for parallel execution
- **Storage:** Minimal
- **External deps:** Claude Code, tmux, Anthropic API key
- **Estimated cost:** Free (you pay for Claude API — but it optimizes token spend)

## Security Assessment
- **Scorecard:** TODO
- **Notes:** Spawns real tmux processes — review what agents can access on your system

## How Tmux Orchestration Works
- **Inside tmux** (`$TMUX` set): reuses current tmux surface for split-pane layouts
- **Inside cmux or plain terminal**: launches detached tmux sessions for workers
- Workers **spawn on-demand and die when done** — no idle resource usage
- Communication via structured JSON request/response (`claim-task` API)
- Artifacts stored at `.omc/artifacts/`, state is file-based (not socket)
- Multi-provider: can run Claude, Codex, and Gemini workers concurrently in separate panes

## Community Sentiment
- **No HN discussion threads** — 0 stories found
- One HN commenter dismissed the broader category as "magic thinking" hype
- 13.9K stars suggests GitHub adoption, but **independent reviews/testimonials are notably absent**
- Marketing-forward: landing page prioritizes feature lists over technical transparency
- **No published benchmarks** for speed/cost claims despite `/benchmark` directory existing

## Limitations & Gotchas
- Requires tmux — may need setup on some systems
- 32 parallel agents = significant API costs if not careful
- Adds complexity on top of Claude Code — learning curve
- Relatively new project, may have rough edges
- **NPM package name mismatch:** repo is "oh-my-claudecode" but publishes as "oh-my-claude-sisyphus"
- Legacy `swarm` syntax removed; must use `/team` commands
- No published benchmarks backing the 3-5x speed / 30-50% cost claims

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| superpowers | Open Source | Methodology-focused (process), not parallelism-focused |
| Claude Code native subagents | Built-in | Simpler but less orchestration control |
| Aider multi-file | Open Source | Different approach, git-centric |

## Learning Value
- **Architecture patterns:** Multi-agent orchestration with staged pipelines and verification loops
- **Interesting techniques:** Smart model routing for cost optimization, tmux-based process isolation
- **Reusable components:** The model routing logic (when to use cheap vs expensive models)

## Links
- Docs: https://ohmyclaudecode.com
- Repo: https://github.com/Yeachan-Heo/oh-my-claudecode
