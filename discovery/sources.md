# Discovery Sources

Where to find production-grade open-source solutions. Agents should check these regularly.

## Tier 1: High-Signal (Check Weekly)

### GitHub Trending
- https://github.com/trending?since=weekly
- Filter: 500+ stars/week, has releases, active issues
- API: unofficial github-trending-api or scrape

### OSSInsight
- https://ossinsight.io
- Collections by category, growth analytics
- API: https://ossinsight.io/docs/api

### Hacker News
- "Show HN" posts with 100+ points
- API: https://hn.algolia.com/api
- Query: `show_hn` tag, sort by points, filter to repos

### Awesome Selfhosted
- https://github.com/awesome-selfhosted/awesome-selfhosted
- Curated, categorized, production-focused
- Watch for new additions via git diff

## Tier 2: Curated Directories (Check Monthly)

### OpenAlternative
- https://openalternative.co
- Maps commercial SaaS → open-source alternatives

### CNCF Landscape
- https://landscape.cncf.io
- Cloud-native tools with maturity levels (sandbox → graduated)

### Runacap ROSS Index
- https://runacap.com/ross-index/
- Fastest-growing open-source startups by star velocity

### Libraries.io
- https://libraries.io
- SourceRank scoring across 40+ package managers

## Tier 3: Community Signals (Passive)

### Newsletters
- Console.dev — weekly, reviews 2-3 tools per issue
- TLDR Open Source — daily highlights
- Changelog News — weekly podcast/newsletter

### Reddit
- r/selfhosted, r/opensource, r/devops, r/homelab
- Sort by top/week, look for "I replaced X with Y" posts

### X/Twitter
- Follow: @github, @ossinsight, @awesome_oss
- Track: "just open-sourced", "moved to open source"

## Filtering Criteria (Must Pass Before Profiling)

A repo must meet ALL of these before getting a full profile:
1. **500+ stars** (social proof of interest)
2. **Commits in last 90 days** (actively maintained)
3. **Has releases/tags** (not just raw commits)
4. **Has a license** (OSI-approved)
5. **Has documentation** (README with setup instructions at minimum)
6. **Responds to issues** (median response < 7 days)
