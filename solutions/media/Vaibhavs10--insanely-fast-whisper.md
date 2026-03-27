---
name: "Insanely Fast Whisper"
repo: "Vaibhavs10/insanely-fast-whisper"
url: "https://github.com/Vaibhavs10/insanely-fast-whisper"
category: "media"
stars: 11826
license: "Apache-2.0"
language: "Jupyter Notebook"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "easy"
---

## What It Does
CLI tool that makes OpenAI Whisper transcription 19x faster on local GPUs. Transcribes 150 minutes of audio in under 98 seconds (vs ~31 minutes unoptimized). Supports transcription, translation, speaker diarization, and word-level timestamps.

## Use Cases
- **Batch transcription:** Process hours of audio in minutes
- **Meeting transcription:** Fast, local, private
- **Content creation:** Subtitle generation for videos
- **Podcast processing:** Transcribe + diarize (who said what)
- **Local/private transcription:** No data sent to cloud APIs

## Who Uses It in Production
- 11.8K stars, widely used in content creation pipelines
- Community-driven, no vendor lock-in

## Tech Stack
- HuggingFace Transformers pipelines
- Optimizations: fp16, batch sizes up to 24, Flash Attention 2, BetterTransformer
- Supports Whisper Large v3 + Distil-Whisper variants
- Works on NVIDIA CUDA + Apple Silicon (MPS)

## How to Deploy
1. `pip install insanely-fast-whisper`
2. `insanely-fast-whisper --file audio.mp3`
3. Add `--diarize` for speaker identification
4. Add `--flash True` for Flash Attention (if supported)

## Deploy Requirements
- **Min RAM:** 8 GB (GPU VRAM)
- **Min CPU:** GPU recommended (NVIDIA or Apple Silicon)
- **External deps:** HuggingFace account for model download
- **Estimated cost:** Free (runs locally)

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** None (0 workflows)
- **Signed releases:** No (0 releases)
- **Contributors:** ~20
- **Last commit:** 2025-10-25 (5+ months stale — may be feature-complete or abandoned)
- **Open issues:** 112
- **Dependency pinning:** Yes (pdm.lock)

## Real Benchmarks by Hardware
| Hardware | Model | Audio | Time | Speed |
|----------|-------|-------|------|-------|
| A100 80GB + FA2 | Large-v3 | 150 min | ~98s | 92x realtime |
| A100 80GB + FA2 | Distil-large-v2 | 150 min | ~78s | 115x realtime |
| RTX 4090 + FA2 | Large-v3 | 10 min | ~8s | 75x realtime |
| M1 Pro (MPS) | Large-v3 | 10 min | ~263s | 2.3x realtime |
| Standard (fp32) | Large-v3 | 150 min | ~31 min | 5x realtime |

**Key insight:** RTX 4090 is **6-12x faster** than Apple's best Silicon for this workload.

## Community Sentiment
- HN skepticism: "Is this just a CLI wrapper around faster-whisper, transformers and distil-whisper?"
- Diarization is NOT native — requires pyannote.audio. **WhisperX is better for diarization.**
- On Apple Silicon, ranks 4th behind fluidaudio-coreml, parakeet-mlx, and mlx-whisper

## Limitations & Gotchas
- GPU required for the "insanely fast" part — CPU is still slow
- Flash Attention 2 requires compatible GPU and high VRAM
- Diarization requires additional pyannote model + HuggingFace token
- Not a real-time streaming solution — batch processing only
- **Apple Silicon performance is mediocre** — whisper.cpp or MLX-based tools are better on Mac
- Essentially a well-packaged CLI over existing HF optimizations (not novel research)

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Whisper (vanilla) | Open Source | 19x slower without optimizations |
| Whisper.cpp | Open Source | C++ implementation, different optimization approach |
| VibeVoice ASR | Open Source | Microsoft's model, handles 60-min with diarization |
| AssemblyAI | Commercial | API-based, easy but costs money |
| Deepgram | Commercial | Real-time streaming, pay per minute |

## Learning Value
- **Architecture patterns:** Stacking multiple inference optimizations for dramatic speedups
- **Interesting techniques:** How fp16 + batching + Flash Attention compound multiplicatively
- **Reusable components:** The optimization stacking pattern is applicable to any transformer inference

## Links
- Repo: https://github.com/Vaibhavs10/insanely-fast-whisper
