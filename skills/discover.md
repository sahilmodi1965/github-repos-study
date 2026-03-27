# Discover Skill — Find New Solutions Worth Profiling

Scan discovery sources for new production-grade open-source solutions and update the watchlist.

## Trigger
Run weekly or on-demand: "discover new solutions" or "what's trending this week?"

## Steps

### 1. Check Trending Sources
Search these in parallel:
- **GitHub Trending** (weekly): web search for "github trending this week" + check github.com/trending
- **HN Show HN** (100+ points): `https://hn.algolia.com/api/v1/search?tags=show_hn&numericFilters=points>100`
- **Product Hunt** (top launches): web search for "product hunt open source this week"

### 2. Filter Against Criteria
From `discovery/sources.md`, a repo must pass ALL:
1. 500+ stars
2. Commits in last 90 days
3. Has releases/tags
4. Has a license (OSI-approved)
5. Has documentation
6. Responds to issues (median < 7 days)

### 3. Check for Duplicates
- Compare against all existing profiles in `solutions/`
- Compare against `discovery/watchlist.md`
- Skip anything already tracked

### 4. Categorize Finds
For each new find, determine:
- **Profile now:** Meets all criteria + has clear production use cases
- **Add to watchlist:** Interesting but too early or missing criteria
- **Skip:** Not relevant to the brain's focus areas

### 5. Update Files
- Add qualifying repos to `discovery/watchlist.md`
- For high-priority finds, run the recon skill immediately
- Report summary of what was found

## Output
- Number of new repos found
- Repos added to watchlist
- Repos profiled (if any were high-priority)
- Notable trends observed
