---
name: "n8n"
repo: "n8n-io/n8n"
url: "https://github.com/n8n-io/n8n"
category: "workflow-automation"
stars: 183000
license: "Sustainable Use License v1.0 (source-available; not fully OSI-approved)"
language: "TypeScript"
last_profiled: "2026-04-06"
production_ready: true
security_score: 7
deploy_complexity: "easy"
---

## What It Does
Self-hostable workflow automation platform with 400+ native integrations and native AI agent support. Connects APIs, databases, and services via a visual node-based editor. Positioned as an open-core alternative to Zapier/Make with full data sovereignty — your automations run on your infrastructure.

## Use Cases
- Automate CRM data sync between HubSpot, Salesforce, and internal DBs
- Build AI agent workflows with LLM nodes (OpenAI, Anthropic, local models)
- ETL pipelines: transform and route data between SaaS tools
- Internal ops automation: Slack alerts, ticket routing, invoice processing
- RAG pipelines: extract docs → embed → store in vector DB
- Customer onboarding workflows triggered by Stripe webhooks

## Who Uses It in Production
- 500,000+ self-hosted deployments globally
- Used by teams at Shopify, Cisco, Siemens (documented case studies)
- n8n Cloud (managed) available for teams wanting zero infra
- One of the top 10 most-starred TypeScript repos on GitHub
- **[2026-04-06 update]** 183K stars (up from 105K in March 2026); latest release v2.14.2 (2026-03-26); 900+ pre-built workflow templates now available

## Tech Stack
- TypeScript + Node.js backend
- Vue.js frontend (workflow editor)
- SQLite (default) or PostgreSQL for production
- Bull/Redis for queue-based execution
- Docker-first deployment
- Native AI integrations: OpenAI, Anthropic, HuggingFace, Ollama

## How to Deploy
1. `docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n n8nio/n8n`
2. Open http://localhost:5678 and create account
3. For production: use docker-compose with PostgreSQL + Redis
4. Configure webhooks, credentials, and first workflow via UI
5. Optional: use n8n Cloud at app.n8n.cloud for managed hosting

## Deploy Requirements
- **Min RAM:** 1 GB (SQLite mode); 2 GB with PostgreSQL
- **Min CPU:** 1 vCPU
- **Storage:** 5 GB minimum; more for execution logs
- **External deps:** Optional: PostgreSQL, Redis (for queue mode)
- **Estimated cost:** Self-hosted ~$5-20/mo VPS; n8n Cloud from $20/mo

## Security Assessment
- **Scorecard:** ~7/10
- **Known CVEs:** Several historical (mostly SSRF and credential exposure) — tracked in advisories; patched promptly
- **Signed releases:** Yes (npm packages signed)
- **Branch protection:** Yes
- **Dependency pinning:** Yes (package-lock.json)
- **SBOM available:** Partial (via npm)
- **Notes:** Credential storage uses AES-256 encryption. SSRF risk if allowing arbitrary webhook URLs — restrict network egress in production. Multi-tenant deployments need careful role-based access setup.

## Limitations & Gotchas
- **License:** Sustainable Use License — free for most use but prohibits offering n8n as a managed service to others without a commercial license. Not OSI-approved.
- Community nodes are unreviewed third-party code — audit before enabling
- Large workflow execution (1000+ items) requires queue mode + Redis
- No built-in audit log in free tier (enterprise feature)
- Complex branching logic can become visually hard to maintain
- Version upgrades occasionally require migration scripts

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Zapier | Commercial ($20/mo+) | Easier UX, more polished, no self-hosting |
| Make (Integromat) | Commercial | Visual-first, strong data mapping, cloud-only |
| Temporal | Open Source | Code-first, durable execution for complex workflows |
| Apache Airflow | Open Source | Python-native, data engineering focus, steeper learning curve |
| Prefect | Open Source | Data pipeline focus, better observability |

## Learning Value
- **Architecture patterns:** Node-based visual workflow composition; credential vault pattern; webhook-to-execution pipeline
- **Interesting techniques:** AI-native node design — structured outputs from LLMs feed directly into downstream nodes
- **Reusable components:** The credentials encryption module; the queue-based execution pattern with Bull

## Links
- Docs: https://docs.n8n.io
- Community: https://community.n8n.io
- Blog: https://blog.n8n.io
