---
name: "VibeVoice"
repo: "microsoft/VibeVoice"
url: "https://github.com/microsoft/VibeVoice"
category: "ai-voice"
stars: 32713
license: "MIT"
language: "Python"
last_profiled: "2026-03-31"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "complex"
---

## What It Does
Three open-source voice AI models from Microsoft Research: TTS (1.5B params, 90-min multi-speaker synthesis), ASR (7B params, 60-min transcription with speaker diarization), and Realtime (0.5B params, ~300ms streaming TTS). MIT-licensed. Outperforms ElevenLabs v3 and Google Gemini 2.5 Pro TTS on listener preference benchmarks.

## Use Cases
- **Audiobook generation:** Multi-speaker, up to 90 minutes in a single pass
- **Podcast creation:** 4 distinct speakers with natural turn-taking
- **Transcription:** 60-minute audio with speaker identification ("Who/When/What")
- **Real-time voice interfaces:** 300ms latency streaming TTS for chatbots/assistants
- **Localization:** 50+ languages supported
- **Replacing ElevenLabs/similar:** Free alternative to $22/month TTS services

## Who Uses It in Production
- Microsoft Research release, widely adopted
- Models on Hugging Face with vLLM inference optimization
- Released in waves: TTS (Aug 2025), Realtime (Dec 2025), ASR (Jan 2026)

## Tech Stack
- Continuous speech tokenizers (Acoustic + Semantic) at 7.5 Hz frame rate
- Next-token diffusion framework (LLM backbone + diffusion heads)
- vLLM for inference optimization
- Hugging Face Transformers
- Finetuning code included

## How to Deploy
1. Download models from Hugging Face
2. Set up vLLM server for inference
3. Requires GPU (H100 recommended for production throughput)
4. API compatible with standard TTS/ASR interfaces

## Deploy Requirements
- **Min RAM:** 16+ GB (model dependent)
- **Min CPU:** GPU required — H100 for production, consumer GPUs for testing
- **Storage:** 10-30 GB for model weights
- **External deps:** CUDA-capable GPU, vLLM
- **Estimated cost:** Self-hosted GPU server ($1-3/hr on cloud) vs ElevenLabs $22/mo. Break-even depends on usage volume.

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** Yes (org-level via microsoft/.github)
- **Branch protection:** No
- **CI/CD:** None (0 workflows)
- **Signed releases:** No (0 releases)
- **Contributors:** ~11
- **Last commit:** 2026-03-27
- **Open issues:** 107
- **Code of Conduct:** Yes (org-level via microsoft/.github)
- **Dependency pinning:** No lockfile (pyproject.toml only)
- **Notes:** Research project, not a production service. Voice synthesis raises ethical concerns (voice cloning, deepfakes). Was pulled once over misuse concerns.

## Quality Benchmarks
- **PESQ:** 3.068 (clean) / 2.848 (other)
- **UTMOS naturalness:** 4.181/5 (clean) / 3.724 (other)
- **Word Error Rate:** 2.00% on LibriSpeech test-clean
- **vs ElevenLabs:** Wins on quality metrics but ElevenLabs has lower latency (150ms vs 300ms) and voice cloning
- **Languages actually trained on:** English and Chinese ONLY. Other 6 listed languages "may result in unexpected audio outputs"

## Community Sentiment
- HN user: quantized GGUF versions "often go off the rails and lose consistency in voice tone or accent"
- "One run often isn't enough and you have to piece the good parts of many separate runs together"
- **Controversy:** Microsoft pulled it Sep 6, 2025 (11 days after release) over deepfake misuse. Community fork appeared immediately. Re-released later.
- **License caveat:** Microsoft explicitly does NOT recommend commercial or real-world deployment — "research use only"

## Limitations & Gotchas
- **"Research use only"** — Microsoft explicitly discourages production/commercial deployment
- Requires significant GPU resources (not a laptop project)
- Model download is large (multi-GB)
- Fine-tuning requires ML expertise
- Long-form synthesis (90 min) needs H100-class hardware
- **Only truly trained on English and Chinese** — other languages are experimental
- Voice cloning ethical considerations — was pulled once already over misuse
- Quantized versions have consistency issues

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| ElevenLabs | Commercial ($22/mo) | Easier to use, API-first, but costs money |
| Bark (Suno) | Open Source | Good quality but shorter form |
| Coqui TTS | Open Source | Community-driven, less capability |
| OpenAI TTS | Commercial | API-only, no self-hosting |
| Whisper (OpenAI) | Open Source | ASR-only, no TTS |

## Learning Value
- **Architecture patterns:** Continuous speech tokenizers at ultra-low frame rates for long-form processing
- **Interesting techniques:** Next-token diffusion combining LLM backbone with diffusion heads, 7.5 Hz tokenization
- **Reusable components:** The tokenizer approach could inspire similar long-form processing in other modalities

## Links
- Docs: https://microsoft.github.io/VibeVoice/
- Models: Hugging Face
- Paper: Microsoft Research
