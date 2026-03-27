# Report Skill — Deep Dive Deployment & Learning Report

Generate a detailed report for a specific solution — how to deploy it, what to learn from it, or how to re-engineer parts of it.

## Trigger
User says: "report on {solution}" or "how do I deploy {solution}" or "what can I learn from {solution}"

## Report Types

### Deploy Report
When the user wants to actually deploy a solution:

```markdown
## Deploy Report: {Solution Name}

### Prerequisites
- [ ] Hardware: {min specs}
- [ ] Accounts/API keys needed: {list}
- [ ] DNS/domain if applicable

### Step-by-Step Deployment
1. ...

### Post-Deploy Checklist
- [ ] Verify health endpoint
- [ ] Connect data sources
- [ ] Set up auth
- [ ] Configure backups
- [ ] Set up monitoring

### Security Hardening
- [ ] ...

### Estimated Time: {hours/days}
### Estimated Cost: {monthly}
```

### Learn Report
When the user wants to understand the architecture:

```markdown
## Architecture Report: {Solution Name}

### System Design
- How it's structured (monolith, microservices, etc.)
- Key design decisions and why

### Interesting Patterns
- {Pattern}: how they did it, why it's clever, where you could reuse it

### Tech Worth Stealing
- Specific libraries, approaches, or techniques worth adopting

### Code Tour
- {file}: what it does and why it matters
```

### Re-engineer Report
When the user wants to build something inspired by it:

```markdown
## Re-engineering Report: {Solution Name}

### Core Value Proposition
What makes this work — the 20% that delivers 80% of value

### Minimum Viable Version
What you'd need to build to replicate the core value:
- ...

### What to Skip
Features that add complexity but aren't core:
- ...

### Suggested Stack
If building from scratch, use:
- ...

### Estimated Build Effort
- MVP: {timeframe}
- Production-grade: {timeframe}
```

## Steps
1. Read the solution's profile from `solutions/`
2. If needed, fetch latest info from the repo (README, docs, releases)
3. Generate the appropriate report type
4. Save report to the conversation (not to disk — reports are point-in-time)
