# Recon Skill — Research & Profile a Repository

When given a GitHub repo (or a topic to find repos for), deeply research it and create a structured profile.

## Trigger
User says: "recon {owner/repo}" or "find solutions for {problem}"

## Steps

### 1. Gather Raw Data
- Read the repo's README, docs, and key source files
- Web search for: "{repo name} review", "{repo name} production", "{repo name} vs"
- Check HN Algolia API for discussions: `https://hn.algolia.com/api/v1/search?query={repo}`
- Check GitHub: stars, issues, contributors, releases, license

### 2. Evaluate Security & Health
Follow the checklist in `discovery/evaluation.md`:
- Query OpenSSF Scorecard API
- Query OSV.dev for vulnerabilities
- Check GitHub community health endpoint
- Manual checks on maintainers, code quality, production signals

### 3. Build the Profile
Use the template at `solutions/PROFILE_TEMPLATE.md` to create a complete profile.
Save to: `solutions/{category}/{owner}--{repo}.md`

### 4. Determine Category
Place in the most specific matching category folder under `solutions/`.
If no category fits, create a new one (lowercase-kebab-case).

### 5. Update Watchlist
If the repo doesn't meet profiling criteria (see `discovery/sources.md`), add it to `discovery/watchlist.md` instead.

## Output
- Created/updated profile file path
- One-paragraph summary of findings
- Production readiness tier (Deploy Now / Deploy with Caution / Learn From / Watch)
