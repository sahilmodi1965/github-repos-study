---
name: "Agent Development Kit (ADK)"
repo: "google/adk-python"
url: "https://github.com/google/adk-python"
category: "ai-agents"
stars: 19100
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-04-20"
production_ready: true
security_score: 8
deploy_complexity: "easy"
---

## What It Does
Google's open-source Python framework for building, evaluating, and deploying production AI agents. Code-first approach: define agent logic in Python, compose multi-agent hierarchies, integrate MCP tools, and deploy to Cloud Run or Vertex AI. Model-agnostic despite being Gemini-optimized; supports human-in-the-loop confirmation flows and built-in evaluation UI.

## Use Cases
- Building multi-agent pipelines where specialized sub-agents handle different tasks
- Enterprise agentic workflows requiring human approval before tool execution
- RAG + agent systems deployed on Google Cloud via Vertex AI Agent Engine
- Replacing manual workflow automation with LLM-driven agents
- Teams already on GCP wanting a Google-native agent SDK with no vendor lock-in

## Who Uses It in Production
- Google internal teams (built by Google DeepMind / Cloud)
- Active community with monthly community calls since Oct 2025
- v1.31.0 released April 17, 2026 — indicates rapid, stable cadence

## Tech Stack
- Python 3.9+ (96% of codebase)
- FastAPI for local agent serving and dev UI
- Vertex AI Code Execution Sandbox for safe code execution
- A2A (Agent-to-Agent) protocol for inter-agent communication
- MCP tool integration built-in
- Deploy targets: Cloud Run (containerized), Vertex AI Agent Engine (managed)

## How to Deploy
1. `pip install google-adk`
2. Create agent: `from google.adk.agents import Agent; agent = Agent(model="gemini-2.0-flash", ...)`
3. Local dev: `adk web` — opens built-in dev UI at localhost for testing/debugging
4. Containerize: `adk deploy cloud_run --project=<gcp-project> --region=<region>`
5. Managed scale: deploy to Vertex AI Agent Engine via `adk deploy vertex_ai`

## Deploy Requirements
- **Min RAM:** 512 MB (local); scales with Vertex AI
- **Min CPU:** 1 vCPU
- **Storage:** Minimal Python package (<100 MB)
- **External deps:** Google API key or GCP project (Vertex AI for production); optional MCP servers
- **Estimated cost:** Free local dev; Vertex AI pricing applies at scale (~$0.002/1K tokens Gemini Flash)

## Security Assessment
- **Scorecard:** ~8/10 (Apache-2.0, Google org, active CI)
- **Known CVEs:** None as of 2026-04-20
- **Signed releases:** Yes (PyPI via Google CI)
- **Branch protection:** Yes (Google org enforces review)
- **Dependency pinning:** Partial (pyproject.toml with version ranges)
- **SBOM available:** Not published separately
- **Notes:** Tool Confirmation (HITL) flow is the key safety mechanism — always enable for destructive tools. Vertex AI sandbox provides code execution isolation. Be mindful of Gemini data handling terms when using managed APIs.

## Limitations & Gotchas
- Best features (Agent Engine, Code Execution sandbox) require GCP — not purely cloud-neutral
- Non-Gemini models need manual configuration; fewer built-in features
- A2A protocol is still maturing — spec may change across minor versions
- Dev UI is for testing only; not a production-facing UI
- Java/Go ADK variants exist but are less mature than Python

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| LangGraph | Open Source | More mature, provider-neutral, steeper learning curve |
| CrewAI | Open Source | Higher-level, role-based agent abstraction |
| AutoGen (Microsoft) | Open Source | Conversation-driven multi-agent, Azure-optimized |
| Dify | Open Source | Visual workflow builder, less code-first |
| openai/codex | Open Source | Terminal-focused, single-agent, not a framework |

## Learning Value
- **Architecture patterns:** Multi-agent hierarchy design with specialized sub-agents — clean reference implementation
- **Interesting techniques:** Tool Confirmation (HITL) guard pattern; A2A protocol for agent-to-agent RPC
- **Reusable components:** The MCP tool integration layer; the agent evaluation harness with built-in UI

## Links
- Docs: https://google.github.io/adk-docs
- PyPI: https://pypi.org/project/google-adk/
- Releases: https://github.com/google/adk-python/releases
