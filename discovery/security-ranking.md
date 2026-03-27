# Security Posture Ranking

All 12 profiled solutions ranked by production security readiness.
Last updated: 2026-03-28

## Ranking

| Rank | Solution | Security Policy | Branch Prot. | CI/CD | Signed | Deps Pinned | Contributors | Posture |
|------|----------|----------------|-------------|-------|--------|-------------|-------------|---------|
| 1 | **twentyhq/twenty** | Yes | Yes | 30 workflows | GPG commits | Yes (yarn.lock) | ~460 | **HIGH** |
| 2 | **FreeCAD/FreeCAD** | Yes | Partial (1/10) | Yes | No | Yes (7/10) | 500+ | **MEDIUM-HIGH** (Scorecard: 6.8/10) |
| 3 | **onyx-dot-app/onyx** | No | Yes | 32 workflows | No | Yes (uv.lock + package-lock) | ~172 | **MEDIUM** |
| 4 | **Yeachan-Heo/oh-my-claudecode** | No | Yes | 6 workflows | No | Yes (package-lock) | ~64 | **MEDIUM** |
| 5 | **virattt/dexter** | No | No | 2 workflows | No | Yes (package-lock + bun.lock) | ~17 | **LOW-MEDIUM** |
| 6 | **datalab-to/chandra** | No | No | 2 workflows | No | Yes (uv.lock) | ~3 | **LOW-MEDIUM** |
| 7 | **microsoft/VibeVoice** | Yes (org) | No | No | No | No | ~11 | **LOW** (research only) |
| 8 | **obra/superpowers** | No | Yes | No | No | No | ~26 | **LOW** (acceptable — it's prompts) |
| 9 | **hacksider/Deep-Live-Cam** | No | No | No | Partial | ~55 | **LOW** | |
| 10 | **mvanhorn/last30days-skill** | No | No | No | No | No | ~8 | **LOW** |
| 11 | **Vaibhavs10/insanely-fast-whisper** | No | No | No | No | Yes (pdm.lock) | ~20 | **LOW** (5mo stale) |
| 12 | **SakanaAI/AI-Scientist-v2** | No | No | No | No | No | ~8 | **VERY LOW** (3mo stale, custom license) |

## Key Findings

- **Only 2/12 have security policies:** Twenty (repo-level) and VibeVoice (org-level via Microsoft)
- **Only 4/12 have branch protection:** Twenty, Onyx, oh-my-claudecode, superpowers
- **0/12 have signed releases** — none use cryptographic signatures on release assets
- **Best overall:** Twenty is the gold standard — security policy, branch protection, 30 CI workflows, GPG commits, CoC, lockfile
- **Only 1/12 in OpenSSF Scorecard:** FreeCAD (6.8/10)

## Production Deployment Tiers (Security-Informed)

| Tier | Solutions | Deploy Guidance |
|------|-----------|-----------------|
| **Deploy with confidence** | Twenty, FreeCAD, Onyx | Strong security posture, active maintenance, production users |
| **Deploy with review** | oh-my-claudecode, Dexter, Chandra | Some security gaps but functional CI, pinned deps |
| **Deploy for personal/dev only** | Superpowers, last30days, insanely-fast-whisper | Low security overhead acceptable for their use case |
| **Learn from, don't deploy** | AI-Scientist-v2, Deep-Live-Cam, VibeVoice | Research projects, ethical concerns, or explicitly not for production |
