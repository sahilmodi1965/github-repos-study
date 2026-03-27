# Match Skill — Find Solutions for a Business Problem

When the user describes a problem, scan all profiled solutions and return ranked matches.

## Trigger
User describes a business problem or asks "what can I use for {X}?"

## Steps

### 1. Understand the Problem
Extract from the user's description:
- **Core need:** What capability is required? (e.g., "AI search over company docs")
- **Scale:** How many users/documents/requests?
- **Constraints:** Budget, hosting preference (cloud/self-hosted), compliance needs
- **Timeline:** How fast does it need to be deployed?

### 2. Scan Solutions
Read all profile files in `solutions/` directories.
For each, score against:
- **Fit** (0-10): How well does this solve the stated problem?
- **Deploy complexity** (from profile): Can it be deployed within the timeline?
- **Security** (from profile): Does the security posture match the constraint?
- **Maturity** (from profile): Is it production-ready or learning-only?

### 3. Check for Gaps
If no profiled solution fits well:
- Search the web for potential solutions
- Check `discovery/watchlist.md` for unproifled candidates
- Suggest running the recon skill on promising finds

### 4. Generate Report
Output a structured comparison:

```markdown
## Problem: {restated problem}

### Top Matches

#### 1. {Solution Name} — Fit: X/10
- **Why it fits:** ...
- **Deploy effort:** ...
- **Security score:** X/10
- **Gotchas:** ...
- **Quick start:** ...

#### 2. {Solution Name} — Fit: X/10
...

### Gaps / Not Covered
- {aspects of the problem no profiled solution covers}

### Suggested Recon
- {repos worth investigating that aren't profiled yet}
```

## Output
Ranked solution report with deployment guidance.
