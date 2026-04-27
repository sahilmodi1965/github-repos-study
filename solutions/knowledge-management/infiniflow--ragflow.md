---
name: "RAGFlow"
repo: "infiniflow/ragflow"
url: "https://github.com/infiniflow/ragflow"
category: "knowledge-management"
stars: 79100
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-04-27"
production_ready: true
security_score: 7
deploy_complexity: "moderate"
---

## What It Does
Open-source RAG engine that combines deep document understanding with agentic capabilities to build a reliable context layer for LLMs. Handles diverse formats (PDF, Word, PPT, Excel, images, web) with template-based chunking that reduces hallucinations via grounded citations. Positions itself as enterprise-grade, not just a prototype library.

## Use Cases
- Enterprise knowledge bases: ingest internal docs, policies, and manuals for LLM Q&A
- Customer support: RAG over product documentation with cited answers
- Legal/compliance: search across contracts and regulations with source traceability
- Research assistant: multi-source synthesis from academic and internal documents
- Agentic pipelines: orchestrate multi-step workflows over ingested knowledge

## Who Uses It in Production
- 79K+ stars — one of the most-starred RAG projects on GitHub
- Active community with 41 releases through April 2026
- Used via Docker Compose in self-hosted enterprise deployments
- Integration partner ecosystem with Confluence, S3, Notion, Google Drive, Discord

## Tech Stack
- Python (45%), TypeScript frontend
- Elasticsearch for BM25 retrieval + vector DB for semantic search
- Docker Compose for all services (API, frontend, storage, index)
- MCP (Model Context Protocol) support for agentic tool use
- Supports GPT-4, Gemini, local Ollama models

## How to Deploy
1. `git clone https://github.com/infiniflow/ragflow && cd ragflow/docker`
2. `docker compose -f docker-compose.yml up -d`
3. Open http://localhost (default) → create admin account
4. Upload documents → select chunking template → build knowledge base
5. Query via UI, REST API, or MCP server integration

## Deploy Requirements
- **Min RAM:** 16 GB (recommended 32 GB for production)
- **Min CPU:** 4 cores
- **Storage:** 50 GB minimum (grows with document corpus)
- **External deps:** Docker ≥24.0.0; optional GPU for embedding acceleration
- **Estimated cost:** ~$20-80/mo VPS for self-hosted; cloud LLM API costs extra

## Security Assessment
- **Scorecard:** ~7/10 (Apache-2.0, frequent releases, active maintainers)
- **Known CVEs:** None critical at time of profiling
- **Signed releases:** GitHub releases with checksums
- **Branch protection:** Yes
- **Dependency pinning:** Yes (requirements.txt pinned)
- **SBOM available:** Partial via Docker image
- **Notes:** All data processed locally — no data leaves your infra by default. LLM API calls go to configured provider. Restrict network egress in air-gapped environments.

## Limitations & Gotchas
- 16 GB RAM floor is steep for small teams — not suitable for a $5 VPS
- Document parsing quality varies by file type; complex PDFs with tables can degrade chunking
- Elasticsearch adds operational complexity vs simpler vector-DB-only setups
- MCP/agent support is newer and less battle-tested than core RAG features
- UI is functional but not polished — expect rough edges in self-hosted setup

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| onyx (Danswer) | Open Source | More polished UI, weaker deep-doc parsing |
| RAG-Anything | Open Source | Library-first, multimodal, lighter-weight |
| LlamaIndex | Open Source | Framework/library, requires more wiring |
| Haystack | Open Source | Pipeline-oriented, less UI, more code-first |
| Azure AI Search | Commercial | Managed, enterprise SLA, no self-hosting |

## Learning Value
- **Architecture patterns:** How to build a full-stack RAG service (ingestion → index → retrieval → generation) with Docker Compose microservices
- **Interesting techniques:** Template-based chunking — domain-specific chunkers (Q&A, paper, law) dramatically outperform naive split-by-size
- **Reusable components:** The document parsing pipeline; the hybrid BM25+vector retrieval scorer

## Links
- Docs: https://ragflow.io/docs
- Discord: https://discord.gg/4XxujFgUN7
- Blog: https://ragflow.io/blog
