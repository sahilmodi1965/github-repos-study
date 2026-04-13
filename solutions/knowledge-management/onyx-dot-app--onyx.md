---
name: "Onyx"
repo: "onyx-dot-app/onyx"
url: "https://github.com/onyx-dot-app/onyx"
category: "knowledge-management"
stars: 26800
license: "MIT"
language: "Python"
last_profiled: "2026-04-13"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "moderate"
---

## What It Does
Self-hosted AI chat platform that connects to 48+ knowledge sources (Slack, Google Drive, Confluence, GitHub, Jira, Salesforce, etc.) and provides AI-powered search and chat over your organization's documents. Works with any LLM — cloud or self-hosted. Formerly known as Danswer.

## Use Cases
- **Company AI assistant:** Employees ask questions, get answers sourced from internal docs with citations
- **Onboarding bot:** New hires search across all company knowledge without knowing where things live
- **Support automation:** Auto-resolve customer queries using internal knowledge base (Ramp claims 93% auto-resolution)
- **Compliance/audit:** Search across all communications and docs with access controls
- **Developer assistant:** Search across GitHub repos, Jira tickets, Confluence docs simultaneously

## Who Uses It in Production
- **Netflix** — 14,000+ employees, company-wide enterprise search
- **Ramp** — thousands of queries/week, 30x ROI claimed
- **Thales Group** — defense/security (highly regulated)
- **UC San Diego** — 37,000 users, human-in-the-loop agent workflows
- Fortune 100 company (unnamed) — 10,000+ employees
- 1,000+ teams total, 125+ code contributors

## Tech Stack
- **Backend:** Python (FastAPI), PostgreSQL, Redis, Vespa (search engine)
- **Frontend:** TypeScript/React
- **Infrastructure:** Docker Compose (12 containers), Nginx, MinIO
- **LLMs:** OpenAI, Anthropic, Google, Azure, AWS Bedrock, Ollama, vLLM
- **Search:** Hybrid vector + knowledge graph (beyond basic RAG)

## How to Deploy
1. Run the install script:
   ```bash
   curl -fsSL https://raw.githubusercontent.com/onyx-dot-app/onyx/main/deployment/docker_compose/install.sh > install.sh
   chmod +x install.sh && ./install.sh
   ```
2. Access at http://localhost:3000
3. Configure LLM provider (API key for OpenAI/Anthropic, or point to Ollama)
4. Add connectors via admin UI (OAuth setup per source)
5. Wait for initial indexing to complete

## Deploy Requirements
- **Min RAM:** 8 GB (4 GB absolute minimum, will struggle)
- **Min CPU:** 4 cores
- **Storage:** 20GB+ depending on indexed content volume
- **External deps:** LLM API key (or Ollama for fully local), OAuth credentials per connector
- **Estimated cost:** Self-hosted on a $40-80/mo VPS + LLM API costs. Cloud version: $20/user/mo.

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None (surprising for a YC company handling enterprise data)
- **Branch protection:** Yes
- **CI/CD:** Yes (32 workflows — strong)
- **Signed releases:** No (binary assets but no signatures)
- **Contributors:** ~172
- **Last commit:** 2026-03-27
- **Open issues:** 296
- **Code of Conduct:** None
- **Dependency pinning:** Yes (uv.lock + package-lock.json)
- **License:** MIT + Onyx Enterprise (dual)
- **Known CVEs:** Permission sync bugs found and patched (PR #4364, #4495)
- **SBOM:** Not published
- **Critical note:** Permission sync (who sees what) is ENTERPRISE-ONLY. On free tier, all indexed content is visible to all users.

## Latest Release & Changes
- **[2026-04-13 update]** Stars jumped to 26.8K (was 19K on 2026-03-28); OpenSearch now default; Canvas Connector data fetching added; voice assistant improvements; encryption key rotation utilities
- **v3.2.1** (Apr 10, 2026) — perm sync start time optimization, NGINX routing fix, Celery Redis connection pooling, configurable file upload sizes, Prometheus metrics for workers
- **v3.2.0** (Apr 9, 2026) — Canvas Connector, refactored admin UI, enhanced monitoring, voice assistant updates
- **v3.1.4** (Apr 10, 2026) — tool call argument streaming, encryption key rotation, OpenSearch enabled by default, Storybook added
- **v3.0.5** (Mar 25, 2026) — completed Vespa-to-OpenSearch migration (FOSS Elasticsearch fork, smaller memory, equal/better search)
- **v2.12.0**: Brave web search provider, auto-summarization of long conversations
- **v2.11.0**: User MCP actions, custom chat backgrounds, macOS desktop app with code signing
- **v2.10.0**: Discord bot, image generation (Gemini), Slack connector restored
- **v2.9.0**: Chrome extension with address-bar quick access, embeddable website widget
- **v2.8.0**: Prompt caching (50-90% LLM cost reduction claim), LLM cost tracking

## Community Sentiment
- **Fortune 100 team** forked Onyx and gave 10K+ employees access to every LLM through single interface
- A deployed user connected Freshdesk, Bookstack, Google Drive, Slack — tech support team uses it daily
- **Criticism:** Admin interface "missing a bit of love" — hard to track processed docs or map results to sources
- **Criticism:** RAG ergonomics worse than AnythingLLM in some workflows
- **Controversy:** MIT core + proprietary "ee" directories drew "enshitification" concerns, though SSO was moved to MIT
- **Missing:** mobile app parity, voice mode, canvas editing

## Limitations & Gotchas
- **Permission sync is Enterprise-only ($50K+/yr)** — on Community Edition all users see everything indexed
- 12 Docker containers is heavy for "just trying it out" — needs a real server, minimum 4 vCPU + 10GB RAM
- Google OAuth enabled by default without clear docs → 502 errors if not configured
- Ollama integration has friction (GitHub issues #998, #1414 — system prompts for OpenAI key even with Ollama)
- Chat history becomes hard to navigate at scale
- Admin UI for tracking indexed documents is rough — hard to tell what's been indexed
- RAG quality depends heavily on source document quality
- **Major migration:** Vespa → OpenSearch in v3.0 (200K chunks/hr migration speed)

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| ChatGPT Enterprise | Commercial | Easier setup, but data goes to OpenAI |
| Glean | Commercial ($$$) | More polished, enterprise-grade, very expensive |
| Perplexity Enterprise | Commercial | Web-focused, less internal doc integration |
| AnythingLLM | Open Source | Simpler, fewer connectors, easier to start |
| PrivateGPT | Open Source | Fully local, but fewer integrations |
| Ragflow | Open Source | More RAG-focused, fewer enterprise features |

## Learning Value
- **Architecture patterns:** Hybrid search (vector + knowledge graph) beyond basic RAG, document-level access control system
- **Interesting techniques:** Multi-step agentic "deep research" mode, connector abstraction pattern (48+ sources with unified interface)
- **Reusable components:** The connector framework could be extracted for any multi-source search project

## Links
- Docs: https://docs.onyx.app
- Discord: Active community (3,000+ members)
- Blog: https://onyx.app/blog
- Pricing: https://onyx.app/pricing
