---
name: "DeepTutor"
repo: "HKUDS/DeepTutor"
url: "https://github.com/HKUDS/DeepTutor"
category: "ai-agents"
stars: 17500
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-04-13"
production_ready: true
security_score: 5  # Academic project, active, limited security hardening
deploy_complexity: "moderate"
---

## What It Does
DeepTutor is an agent-native personalized learning platform that deploys autonomous AI tutors capable of adapting to individual learning styles. It provides five distinct interaction modes — Chat, Deep Solve, Quiz Generation, Deep Research, and Math Animator — unified in a single context-aware workspace backed by persistent memory and a personal RAG knowledge base.

## Use Cases
- Corporate L&D: Turn internal documentation into interactive AI tutoring sessions
- EdTech products: Embed as a white-label AI tutoring backend
- Personal learning: Upload textbooks, papers, or course materials and get a personalized curriculum
- Exam prep: Auto-generate quizzes and flashcards from any uploaded content
- Research assistance: Multi-agent deep research mode decomposes complex questions with citations

## Who Uses It in Production
- HKUDS Research Group (Hong Kong University) — origin lab
- Growing community adoption post-viral trending on GitHub (17.5K stars, April 2026)
- Primarily used by developers building EdTech products and self-learners

## Tech Stack
- Backend: Python 3.11+, FastAPI
- Frontend: Next.js 16, React 19
- LLMs: Provider-agnostic (OpenAI, Anthropic, local Ollama)
- Embeddings: Configurable (OpenAI, HuggingFace)
- RAG: Custom vector store + retrieval pipeline
- Math rendering: MathJax / LaTeX animation engine

## How to Deploy
1. `git clone https://github.com/HKUDS/DeepTutor.git && cd DeepTutor`
2. Guided setup: `python scripts/start_tour.py` (recommended — walks through LLM/embedding config)
3. Manual: `pip install -e ".[server]"`, copy `.env.example` to `.env`, configure LLM keys
4. Start backend: `python -m deeptutor.api.run_server`
5. Start frontend: `cd web && npm install && npm run dev -- -p 3782`
6. Access at `http://localhost:3782`
7. Docker alternative: `docker compose -f docker-compose.ghcr.yml up -d`

## Deploy Requirements
- **Min RAM:** 4 GB (8 GB recommended for local LLM models)
- **Min CPU:** 2 vCPU
- **Storage:** 2 GB for app + model files if using local embeddings
- **External deps:** LLM provider API key (OpenAI/Anthropic) OR local Ollama; optional search provider for Deep Research mode
- **Estimated cost:** ~$5–15/month on a 2 vCPU VPS + LLM API costs

## Security Assessment
- **Scorecard:** ~5/10 (estimated; academic project, lacks enterprise security hardening)
- **Known CVEs:** None as of 2026-04-13
- **Signed releases:** No (GitHub releases only, no GPG signing)
- **Branch protection:** Likely minimal (small academic team)
- **Dependency pinning:** Partial
- **SBOM available:** No
- **Notes:** Designed for internal/self-hosted use. Do not expose to public internet without auth layer. API keys stored in `.env` — ensure proper secrets management in production.

## Limitations & Gotchas
- Deep Research mode requires a web search provider (adds cost and latency)
- Math Animator is impressive but may fail on very complex LaTeX expressions
- Memory persistence is file-based by default — needs PostgreSQL for multi-user production
- No built-in auth system — wrap with a reverse proxy (Nginx + OAuth) before exposing publicly
- Heavy dependency stack: both Python and Node.js environments required

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Khanmigo (Khan Academy) | Commercial SaaS | Polished product, no self-hosting |
| Quizlet Q-Chat | Commercial | Flashcard-focused, limited document ingestion |
| Perplexity | Commercial | Research focus only, no tutoring modes |
| AnkiGPT | Open Source | Flashcard generation only, no full tutor |
| Open WebUI | Open Source | Generic LLM UI, no tutoring-specific workflows |

## Learning Value
- **Architecture patterns:** Multi-mode agent orchestration within a single unified context — each "mode" is a separate agent graph sharing memory
- **Interesting techniques:** Guided Learning flow converts arbitrary documents into structured curricula using LLM planning + RAG retrieval
- **Reusable components:** Quiz generation pipeline, math animator, RAG knowledge base module are all independently useful

## Links
- Docs: https://github.com/HKUDS/DeepTutor#readme
- Discord/Community: GitHub Discussions
- Blog/Changelog: https://github.com/HKUDS/DeepTutor/releases
