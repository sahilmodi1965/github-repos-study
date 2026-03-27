---
name: "AI Scientist v2"
repo: "SakanaAI/AI-Scientist-v2"
url: "https://github.com/SakanaAI/AI-Scientist-v2"
category: "ai-research"
stars: 2819
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-03-28"
production_ready: false
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "complex"
---

## What It Does
Autonomous scientific research system that generates hypotheses, designs and runs experiments, analyzes results, and writes complete scientific papers — all without human intervention. Produced the first workshop paper written entirely by AI accepted through peer review (ICLR 2025 workshop). Uses best-first tree search to explore experimental directions.

## Use Cases
- **ML research automation:** Explore research questions, run experiments, produce papers
- **Hypothesis testing at scale:** Parallel exploration of multiple experimental directions
- **Literature review:** Automated Semantic Scholar integration for novelty checking
- **Research acceleration:** $20-30 per full research run

## Who Uses It in Production
- Research tool, not a production service
- **3 papers submitted to ICBINB workshop at ICLR 2025:** 1 accepted (scores 6,7,6 — top ~45%), 2 rejected
- Sakana themselves: "none of the 3 papers passed our internal bar for ICLR conference track"
- This was a **workshop** (60-70% acceptance rate), not main conference (20-30%)
- v1 paper published in **Nature**
- Created by SakanaAI (well-funded AI research lab)

## Tech Stack
- Best-first tree search (BFTS) guided by experiment manager agent
- Semantic Scholar API for literature review
- Supports OpenAI, Gemini, Claude as underlying LLM
- Configurable parallel workers per exploration path

## How to Deploy
1. Clone repo, install Python dependencies
2. Configure LLM API keys
3. Define research scope/template
4. Run — costs ~$20-30 per full research run

## Deploy Requirements
- **Min RAM:** 16 GB
- **Min CPU:** Multi-core for parallel workers
- **External deps:** LLM API keys, compute for experiments
- **Estimated cost:** $20-30 per research run (LLM API costs)

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** None (0 workflows)
- **Signed releases:** No (0 releases)
- **Contributors:** ~8
- **Last commit:** 2025-12-19 (3+ months stale)
- **Open issues:** 50
- **Dependency pinning:** No (unpinned requirements.txt)
- **License:** Custom (AI Scientist Source Code License v1.0) — NOT OSI-approved
- **Security posture: LOW**

## Cost Per Run
| Phase | Cost |
|-------|------|
| Ideation (brainstorming + Semantic Scholar novelty check) | ~$2-5 |
| Experimentation (agentic tree search, Claude 3.5 Sonnet) | $15-20 |
| Write-up (paper generation + citations) | ~$5 |
| **Total per paper** | **$15-25** |

## Quality Concerns
- **Hallucination risk:** LLMs generate plausible but unverifiable claims; in rare cases, entire results are hallucinated
- **Low execution accuracy:** Code-to-experiment translation succeeds only 16.9-55.6% on benchmarks
- **Citation errors:** Difficulty finding/citing relevant sources; sometimes duplicates figures
- **Shallow experiments:** "Results often lack the depth and accuracy typical in the ML community"
- Papers should be viewed as "suggestions for promising ideas," not reliable contributions

## Limitations & Gotchas
- Focused on ML domains — not general-purpose scientific research
- Paper quality is workshop-level, not top-conference level
- Expensive if running many parallel explorations
- Requires understanding of ML to evaluate outputs
- **Hallucination is a real risk** — entire results can be fabricated
- **Code execution success rate is low** (16.9-55.6%)
- Visualization problems: illegible charts, suboptimal layouts

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Manual research | Traditional | Higher quality, much slower |
| Elicit | Commercial | Research assistant, not autonomous |
| Consensus | Commercial | Literature review, not experiment-running |
| OpenScholar | Open Source | Literature synthesis, not end-to-end research |

## Learning Value
- **Architecture patterns:** Best-first tree search for agentic exploration — applicable beyond science
- **Interesting techniques:** Automated novelty checking via Semantic Scholar, experiment manager agent pattern
- **Reusable components:** The BFTS exploration pattern could be applied to any multi-path decision problem

## Links
- Repo: https://github.com/SakanaAI/AI-Scientist-v2
- Paper: Associated ICLR 2025 workshop paper
