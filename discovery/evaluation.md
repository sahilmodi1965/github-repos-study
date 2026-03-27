# Security & Production Readiness Evaluation

How to vet an open-source repo before recommending it for deployment.

## Automated Checks (APIs)

### 1. OpenSSF Scorecard (Primary Security Score)
```
GET https://api.securityscorecards.dev/projects/github.com/{owner}/{repo}
```
Key checks and what they mean:
- **Maintained** — commits in last 90 days
- **Branch-Protection** — requires reviews, no force push to main
- **Code-Review** — PRs get reviewed before merge
- **CI-Tests** — automated tests run on PRs
- **Signed-Releases** — releases are cryptographically signed
- **Pinned-Dependencies** — deps pinned to exact versions/hashes
- **Vulnerabilities** — no known unfixed vulns
- **SAST** — static analysis runs in CI
- **Security-Policy** — SECURITY.md exists
- **Dangerous-Workflow** — no untrusted code execution in CI

**Scoring:** 0-10 per check. Target: 7+ aggregate for production use.

### 2. Vulnerability Scan
```
POST https://api.osv.dev/v1/query
{"package": {"name": "...", "ecosystem": "..."}}
```
Also check: `GET https://api.deps.dev/v3alpha/projects/github.com/{owner}/{repo}`

### 3. GitHub Repo Health
```
GET https://api.github.com/repos/{owner}/{repo}
```
Extract: open_issues_count, has_wiki, has_discussions, license, archived, fork count

### 4. Community Health
```
GET https://api.github.com/repos/{owner}/{repo}/community/profile
```
Checks: code_of_conduct, contributing, issue_template, pull_request_template, license, readme

## Manual Checks (Agent Does These)

### Maintainer Assessment
- [ ] More than 1 active maintainer (bus factor > 1)
- [ ] Maintainers are identifiable (not anonymous-only)
- [ ] Contributors from multiple organizations
- [ ] Maintainers respond to security reports

### Code Quality Signals
- [ ] Has tests (test/ or tests/ directory exists)
- [ ] CI/CD pipeline defined (.github/workflows/ or similar)
- [ ] No hardcoded secrets in codebase
- [ ] Dependencies are reasonable (not 500 transitive deps for a simple tool)

### Production Signals
- [ ] Has a CHANGELOG or release notes
- [ ] Follows semver (has reached 1.0+)
- [ ] Docker/Helm/deployment configs provided
- [ ] Monitoring/observability hooks (health endpoints, metrics)
- [ ] Known production users (listed on README or website)

### Red Flags (Auto-Reject)
- Archived repo
- No commits in 6+ months with open security issues
- License is "source available" masquerading as open-source
- Single anonymous maintainer with no community
- README is mostly marketing with no technical substance
- Requires phoning home or telemetry that can't be disabled

## Production Readiness Tiers

| Tier | Criteria | Example |
|------|----------|---------|
| **Deploy Now** | Scorecard 7+, known production users, stable releases, good docs | Onyx, Twenty, FreeCAD |
| **Deploy with Caution** | Scorecard 5-7, growing community, some rough edges | Dexter, Chandra |
| **Learn From / Re-engineer** | Interesting architecture but not production-stable | AI-Scientist-v2, Deep-Live-Cam |
| **Watch** | Too early but high potential | New repos < 6 months old |
