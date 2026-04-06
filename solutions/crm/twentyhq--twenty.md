---
name: "Twenty"
repo: "twentyhq/twenty"
url: "https://github.com/twentyhq/twenty"
category: "crm"
stars: 43600
license: "AGPL-3.0"
language: "TypeScript"
last_profiled: "2026-04-06"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "moderate"
---

## What It Does
Open-source CRM built as a modern alternative to Salesforce. Provides contact/company management, deal pipelines, email integration, calendar events, and workflow automation with a clean UX inspired by Notion and Linear. Fully self-hostable with custom objects and fields.

## Use Cases
- **Sales teams** needing CRM without Salesforce costs ($25-300/user/mo savings)
- **Startups** wanting full data ownership and self-hosting
- **Organizations** needing custom data models (custom objects/fields)
- **Teams migrating off** HubSpot, Pipedrive, or Salesforce
- **Developers** wanting a CRM they can extend via API/plugins

## Who Uses It in Production
- 43.6K stars (up from 41.9K on 2026-03-28), strong community adoption
- Active Hacktoberfest participation indicates healthy contributor base
- **[2026-04-06 update]** Latest release v1.20.0 (2026-03-31); 5.8K forks; 11,252 commits — active development velocity confirmed

## Tech Stack
- TypeScript monorepo (Nx)
- Backend: NestJS, PostgreSQL, Redis, BullMQ (background jobs)
- Frontend: React, Jotai (state), Linaria (CSS-in-JS)
- API: GraphQL
- Supports custom objects/fields, RBAC, plugin system

## How to Deploy
1. Docker Compose for self-hosted
2. Or use Twenty Cloud (hosted version)
3. Configure PostgreSQL and Redis
4. Set up email integration (IMAP/SMTP)

## Deploy Requirements
- **Min RAM:** 4 GB
- **Min CPU:** 2 cores
- **Storage:** 10GB+ depending on data volume
- **External deps:** PostgreSQL, Redis
- **Estimated cost:** Self-hosted: $20-40/mo VPS. Cloud: varies.

## Current Integrations
- **Live now:** Zapier (triggers on record CRUD), REST API, GraphQL API, Webhooks, Chrome extension, email sync (Gmail/Outlook), calendar sync (Google Calendar)
- **Workflow automation live:** triggers on record create/update/delete, manual triggers, iterator nodes, webhook triggers, scheduled workflows
- **Planned Q3/Q4 2026:** WhatsApp, Telegram, Slack, LinkedIn, Google Contacts/Tasks/Drive, Salesforce/HubSpot/Pipedrive migrations, Mailchimp, Twilio, DocuSign, SSO (Okta, Keycloak)

## Community Sentiment
- HN: praised for clean UI and less bloat than Salesforce
- Salesforce consultant noted "the CRM part is easy to build; the hard part is the ecosystem/extensibility"
- Users want quotes/invoicing and document generation — acknowledged gaps vs Freshsales
- **vs Attio:** Twenty is open-source and self-hostable but earlier-stage. Attio is AI-native with more mature automation but closed-source and relies on Zapier (extra cost)

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** Yes (.github/SECURITY.md) — BEST among all 12 repos
- **Branch protection:** Yes
- **CI/CD:** Yes (30 workflows — strong)
- **Signed releases:** No, but commits are GPG-signed
- **Contributors:** ~460 (largest community)
- **Last commit:** 2026-03-27
- **Open issues:** 107
- **Code of Conduct:** Yes
- **Dependency pinning:** Yes (yarn.lock)
- **Security posture: HIGHEST of all 12 profiled repos**

## Limitations & Gotchas
- AGPL-3.0 license — copyleft implications if you modify and distribute
- Younger than Salesforce — fewer integrations and less battle-tested at enterprise scale
- Custom objects/fields add complexity
- Email integration setup can be finicky
- **Native integrations not shipping until Q3/Q4 2026** — currently API-first (Zapier bridge)
- Missing: quotes/invoicing, document generation

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Salesforce | Commercial ($$$) | Industry standard but expensive and bloated |
| HubSpot | Commercial | Free tier exists, but lock-in |
| Attio | Commercial | Modern UX, but closed source |
| EspoCRM | Open Source | PHP-based, less modern UX |
| SuiteCRM | Open Source | Mature but dated interface |

## Learning Value
- **Architecture patterns:** TypeScript monorepo with Nx, GraphQL API layer, custom object/field system
- **Interesting techniques:** How to build a flexible data model that supports user-defined objects
- **Reusable components:** The custom objects architecture, GraphQL schema generation

## Links
- Docs: https://twenty.com/developers
- Community: Discord, GitHub Discussions
