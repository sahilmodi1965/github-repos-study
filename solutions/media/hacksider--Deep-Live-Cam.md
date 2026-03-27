---
name: "Deep-Live-Cam"
repo: "hacksider/Deep-Live-Cam"
url: "https://github.com/hacksider/Deep-Live-Cam"
category: "media"
stars: 82905
license: "AGPL-3.0"
language: "Python"
last_profiled: "2026-03-28"
production_ready: false
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "moderate"
---

## What It Does
Real-time face-swapping tool: one source photo → live webcam feed or video with that face, replicating pose, lighting, and expressions. No model training needed. Supports mouth masking and multi-face swapping. Built-in ethical guardrails block nudity/sensitive content.

## Use Cases
- Live content creation and streaming entertainment
- Video production and prototyping
- Meme generation
- Privacy/anonymization in video content
- **Caution:** Deepfake potential — significant ethical considerations

## Who Uses It in Production
- Viral in Aug 2024 — videos of people "becoming" celebrities on webcam
- 82K+ stars, one of the most-starred AI repos
- Primarily used for entertainment/content creation

## Tech Stack
- InsightFace inswapper_128_fp16 (face swap) + GFPGANv1.4 (face enhancement)
- GPU support: NVIDIA CUDA, AMD DirectML, Intel OpenVINO, Apple CoreML, CPU fallback
- Frame-by-frame live video processing

## How to Deploy
1. Clone repo, install Python dependencies
2. Download model weights (InsightFace, GFPGAN)
3. Run with webcam or video input
4. GPU recommended for real-time performance

## Deploy Requirements
- **Min RAM:** 8 GB
- **Min CPU:** GPU strongly recommended (NVIDIA preferred)
- **External deps:** InsightFace models, GFPGAN models
- **Estimated cost:** Free (runs locally)

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** None (0 workflows)
- **Signed releases:** No (tag-only releases)
- **Contributors:** ~55
- **Last commit:** 2026-03-27
- **Open issues:** 101
- **Dependency pinning:** Partial (mostly pinned with == but some unpinned)

## GPU Performance
| Hardware | Status | Notes |
|----------|--------|-------|
| NVIDIA CUDA 12.8 | Best | Recommended, forced GPU on laptops |
| AMD/Intel DirectML | Windows only | Functional, less optimized |
| Apple Silicon CoreML | Supported | Python 3.10 required, lower perf |
| CPU fallback | Works | Significantly slower |

**No published FPS benchmarks.** Known GPU detection issues (GitHub #1217).

## Ethical & Legal Landscape
- **NSFW filter:** Uses OpenNSFW2 model — mandatory but can be disabled (discouraged)
- **TAKE IT DOWN Act** (signed May 2025): first US federal statute targeting non-consensual intimate deepfakes
- 10+ US states have deepfake-specific legislation
- HN community (251 points): "Technically impressive but I fail to see a good use case not related to propaganda or scam"
- NSFW filter criticized as performative

## Limitations & Gotchas
- **Serious ethical/legal risk** — deepfake creation tool with active legislation targeting misuse
- AGPL-3.0 license — copyleft
- Quality depends on lighting, angle, and source photo quality
- Real-time performance requires decent GPU
- Built-in content filters may block legitimate use cases
- Python 3.10-3.11 specifically required (especially macOS)
- CLI mode "unmaintained" per docs
- Model download ~300MB

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| FaceFusion | Open Source | Similar capabilities, different approach |
| DeepFaceLab | Open Source | Older, requires training |
| Reface App | Commercial | Mobile app, simpler but less capable |

## Learning Value
- **Architecture patterns:** Two-model pipeline (swap + enhance) for real-time video processing
- **Interesting techniques:** Frame-by-frame processing with multi-backend GPU support
- **Reusable components:** The GPU backend abstraction (CUDA/DirectML/OpenVINO/CoreML) pattern

## Links
- Repo: https://github.com/hacksider/Deep-Live-Cam
