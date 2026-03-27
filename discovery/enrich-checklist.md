# Enrichment Checklist

When enriching or updating a solution profile, run through these steps:

## Automated (API-based)
- [ ] OpenSSF Scorecard: `https://api.securityscorecards.dev/projects/github.com/{owner}/{repo}`
- [ ] GitHub repo stats: stars, forks, open issues, last commit date
- [ ] OSV.dev vulnerability check: `POST https://api.osv.dev/v1/query`
- [ ] deps.dev check: `https://api.deps.dev/v3alpha/projects/github.com/{owner}/{repo}`

## Research (web search)
- [ ] HN discussions: `https://hn.algolia.com/api/v1/search?query={repo_name}`
- [ ] Reddit mentions: search r/selfhosted, r/opensource, r/devops
- [ ] Latest release / changelog
- [ ] Real user testimonials (not just README claims)
- [ ] Known production deployments
- [ ] Benchmark data (if applicable)

## Manual Assessment
- [ ] Read the actual README and docs (not just summaries)
- [ ] Check GitHub Issues for recurring complaints
- [ ] Verify license implications for commercial use
- [ ] Assess maintainer health (bus factor, response time)
- [ ] Check for any legal/ethical concerns

## Profile Update
- [ ] Update frontmatter (stars, security_score, last_profiled date)
- [ ] Add community sentiment section with sourced quotes
- [ ] Update limitations with real user complaints
- [ ] Add benchmark data if found
- [ ] Note any breaking changes or migrations
