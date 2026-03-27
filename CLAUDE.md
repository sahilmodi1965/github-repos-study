# Open Source Solutions Brain

Personal knowledge base and recon system for production-grade open-source solutions.

## Purpose
- Agents continuously research, profile, and evaluate open-source repos
- When Sahil brings a business problem, match it to vetted solutions
- Output: actionable reports — learn from it, deploy it, or re-engineer parts

## Project Structure
```
solutions/           # Deep profiles of vetted open-source solutions (YAML + MD)
  {category}/        # Grouped by domain (ai-agents, crm, voice, ocr, etc.)
    {repo-name}.md   # One file per solution — structured profile
discovery/
  sources.md         # Where to look for new solutions
  evaluation.md      # How to score/vet a repo before profiling
  watchlist.md       # Repos spotted but not yet fully profiled
skills/
  recon.md           # Skill: research and profile a new repo
  match.md           # Skill: match a business problem to solutions
  report.md          # Skill: generate deployment/learning report
```

## How It Works

### Adding Solutions
1. Discover a repo (trending, HN, newsletter, user input)
2. Run the recon skill → deep profile gets created in solutions/
3. Profile includes: what it does, use cases, deploy method, security score, limitations, competitors

### Matching Problems
1. User describes a problem: "client needs AI search over their docs"
2. Match skill scans all profiles in solutions/
3. Returns ranked matches with: fit score, deploy complexity, security notes, quick-start steps

### Continuous Enrichment
- Agents can update profiles with new info (version bumps, security advisories, community growth)
- Watchlist tracks repos spotted but not yet profiled

## Conventions
- Solution profiles use consistent frontmatter (see solutions/ for schema)
- Categories are lowercase-kebab-case
- One repo = one file, named {owner}--{repo}.md
- Security evaluation uses OpenSSF Scorecard signals + manual notes
- All dates in YYYY-MM-DD format

## Key APIs (all free)
- GitHub REST/GraphQL API — repo metadata
- OSSInsight API — trending and analytics
- OpenSSF Scorecard API — security scoring (api.securityscorecards.dev)
- OSV.dev API — vulnerability database
- deps.dev API — dependencies, licenses, scorecard in one place
- Libraries.io API — SourceRank health score
- HN Algolia API — community discussion tracking
