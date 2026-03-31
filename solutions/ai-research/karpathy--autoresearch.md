---
name: "autoresearch"
repo: "karpathy/autoresearch"
url: "https://github.com/karpathy/autoresearch"
category: "ai-research"
stars: 53500
license: "MIT"
language: "Python"
last_profiled: "2026-03-31"
production_ready: true
security_score: 6
deploy_complexity: "moderate"
---

## What It Does
Autonomous ML research agent that runs self-directed research loops on a single GPU: propose a hypothesis, implement a training experiment, evaluate results, iterate with feedback. Created by Andrej Karpathy. Turns a single machine into a continuous ML research engine without human supervision between cycles.

## Use Cases
- Run overnight autonomous hyperparameter and architecture search experiments
- Generate novel ML research directions with automated evaluation
- Rapid baseline benchmarking across model variants on a fixed dataset
- Academic research acceleration — complete a week of ablations in hours
- Self-directed literature-informed experiment design

## Who Uses It in Production
- Academic labs running continuous overnight experiments
- AI startups using it for rapid model iteration
- ~53,500 GitHub stars indicating very wide adoption in ML community
- Karpathy's brand ensures heavy scrutiny and quality

## Tech Stack
- Python (primary)
- PyTorch / HuggingFace Transformers for model training
- LLM backbone (Claude/GPT-4) for hypothesis generation and interpretation
- SQLite or local filesystem for experiment logging
- Single-GPU optimized — no cluster required

## How to Deploy
1. `git clone https://github.com/karpathy/autoresearch && cd autoresearch`
2. `pip install -r requirements.txt`
3. Set `ANTHROPIC_API_KEY` or `OPENAI_API_KEY`
4. `python autoresearch.py --task "improve CIFAR-10 accuracy" --budget 10`
5. Monitor logs — agent proposes, trains, evaluates, repeats

## Deploy Requirements
- **Min RAM:** 16 GB system RAM
- **Min CPU:** 8-core modern CPU
- **Storage:** 20+ GB for datasets + experiment logs
- **External deps:** NVIDIA GPU (24GB VRAM recommended); API key for LLM backbone
- **Estimated cost:** GPU cloud ~$0.50-2/hr + LLM API calls (~$5-20/research run)

## Security Assessment
- **Scorecard:** ~6/10
- **Known CVEs:** None
- **Signed releases:** No
- **Branch protection:** Yes (main branch)
- **Dependency pinning:** requirements.txt with pinned versions
- **SBOM available:** No
- **Notes:** Code execution risk — the agent writes and runs Python training scripts autonomously. Should run in a sandboxed container. LLM API key exposure is the primary credential risk.

## Limitations & Gotchas
- Runs training loops autonomously — unconstrained budgets can rack up significant GPU costs
- LLM backbone quality directly limits hypothesis quality; GPT-4/Claude required for best results
- Results are noisy — automated research doesn't replace human scientific judgment
- No built-in hardware multi-GPU support (single GPU by design)
- Experiment reproducibility requires careful seed management

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| SakanaAI/AI-Scientist-v2 | Open Source | Full paper-writing pipeline; heavier infra, writes LaTeX |
| microsoft/agent-lightning | Open Source | Focused on LLM training optimization, not research loops |
| OpenAI o3 research mode | Commercial | Cloud-only, no local training execution |
| AutoML (Google/AWS) | Commercial | Hyperparameter tuning only, no hypothesis generation |

## Learning Value
- **Architecture patterns:** Agent-as-researcher loop: propose → implement → evaluate → feedback → propose
- **Interesting techniques:** LLM-generated Python code executed in constrained subprocess; result parsing back into natural language for next hypothesis
- **Reusable components:** The experiment logging format and hypothesis-to-code generation pipeline

## Links
- Docs: https://github.com/karpathy/autoresearch/blob/main/README.md
- Discussion: Karpathy's X/Twitter threads on autonomous research
- Related: AI-Scientist (Sakana AI) for comparison
