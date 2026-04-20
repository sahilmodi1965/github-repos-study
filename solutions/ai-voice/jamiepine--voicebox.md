---
name: "Voicebox"
repo: "jamiepine/voicebox"
url: "https://github.com/jamiepine/voicebox"
category: "ai-voice"
stars: 21500
license: "MIT"
language: "TypeScript"
last_profiled: "2026-04-20"
production_ready: true
security_score: 6
deploy_complexity: "easy"
---

## What It Does
Local-first, open-source voice synthesis studio: voice cloning, text-to-speech across 7 engines, audio effects, and multi-voice project editing — all on your own machine, no cloud uploads. Positioned as a self-hosted ElevenLabs alternative with a full desktop GUI (Mac/Windows) and Docker/REST API for headless integration.

## Use Cases
- Game dialogue and NPC voice generation without per-character cloud costs
- Podcast and audiobook production with voice cloning from a short audio sample
- Privacy-sensitive voice synthesis (legal, medical, corporate — data never leaves the machine)
- Accessibility tools: custom voice assistants for specific users
- Content localization: 23 languages across supported TTS engines
- Developer integration via REST API for programmatic voice generation pipelines

## Who Uses It in Production
- 44 contributors, 21.5K stars, 20 releases as of April 2026
- Community-driven; no publicly named enterprise deployments yet
- Active issue tracker (228 open issues) with maintained response cadence

## Tech Stack
- Frontend: Tauri (Rust desktop shell) + React + TypeScript + Tailwind CSS
- Backend: FastAPI (Python 3.11+)
- TTS engines: Qwen3-TTS, Qwen CustomVoice, LuxTTS, Chatterbox, TADA, Kokoro
- Audio effects: Pedalboard (Spotify's audio DSP library)
- Transcription: Whisper / Whisper Turbo
- Inference: MLX (Apple Silicon), PyTorch (CUDA/ROCm/XPU), CPU fallback
- Storage: SQLite + local filesystem

## How to Deploy
1. Download DMG (macOS) or MSI (Windows) from GitHub Releases
2. Or Docker: `docker compose up` (headless server + REST API)
3. For dev: `git clone`, install Bun + Rust + Python 3.11+, then `just setup && just dev`
4. Linux: build from source via instructions at voicebox.sh/linux-install
5. Access REST API at `localhost:8888` for programmatic generation

## Deploy Requirements
- **Min RAM:** 4 GB (8 GB+ recommended for larger models like Qwen3-TTS)
- **Min CPU:** Any modern CPU; GPU strongly recommended for real-time generation
- **Storage:** 2–10 GB depending on models downloaded
- **External deps:** None (fully offline); optional GPU drivers for acceleration
- **Estimated cost:** $0 self-hosted; GPU cloud instance ~$0.50–2/hr if needed

## Security Assessment
- **Scorecard:** ~6/10 (MIT, individual developer, SECURITY.md present)
- **Known CVEs:** None as of 2026-04-20
- **Signed releases:** Not formally signed (GitHub Releases with binary downloads)
- **Branch protection:** Unknown (individual repo)
- **Dependency pinning:** Partial (Cargo.lock for Rust; Python deps via pyproject.toml)
- **SBOM available:** No
- **Notes:** All processing local — strong privacy profile. REST API has no auth by default; bind to localhost only or add reverse proxy auth in networked deployments. Vet model provenance (Hugging Face downloads on first run).

## Limitations & Gotchas
- Linux has no pre-built binary — source build required (non-trivial)
- Paralinguistic tags (laughter, sighs) only work in Chatterbox Turbo; other engines render them as literal text
- Real-time streaming audio generation is on the roadmap but not yet implemented
- GPU strongly recommended; CPU inference is very slow for larger models
- Voice cloning quality varies significantly by source audio quality and duration

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| ElevenLabs | Commercial SaaS | Higher quality, cloud-only, per-character pricing |
| Coqui TTS | Open Source | No GUI, Python API only, less active (archived) |
| XTTS-v2 (Coqui) | Open Source Model | Raw model, no studio UI |
| F5-TTS | Open Source | CLI-focused, simpler feature set |
| AllTalk TTS | Open Source | Similar local studio, fewer engines |

## Learning Value
- **Architecture patterns:** Tauri + FastAPI desktop app split — Rust handles desktop shell, Python handles ML inference; clean boundary for AI desktop app architecture
- **Interesting techniques:** Generation version tracking with lineage graph; async queue with SSE streaming for non-blocking long audio jobs
- **Reusable components:** The FastAPI REST API layer is standalone; Pedalboard integration for audio DSP in Python pipelines

## Links
- Docs: https://github.com/jamiepine/voicebox#readme
- Site: https://voicebox.sh
- Releases: https://github.com/jamiepine/voicebox/releases
