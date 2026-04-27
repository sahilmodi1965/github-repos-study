---
name: "RAG-Anything"
repo: "HKUDS/RAG-Anything"
url: "https://github.com/HKUDS/RAG-Anything"
category: "knowledge-management"
stars: 18900
license: "MIT"
language: "Python"
last_profiled: "2026-04-27"
production_ready: true
security_score: 6
deploy_complexity: "easy"
---

## What It Does
Multimodal RAG framework built on LightRAG that handles text, images, tables, and equations in a single unified pipeline. Eliminates the need for multiple specialized parsers — one library processes PDFs, Office docs, images, and mixed-content files end-to-end, building a multimodal knowledge graph with hybrid vector+graph retrieval.

## Use Cases
- Document Q&A over complex PDFs with embedded charts, tables, and math (research papers, technical manuals)
- Knowledge graph construction from heterogeneous corporate document libraries
- Multi-modal search: queries that need image + text evidence from the same document
- RAG pipelines where you control the stack (no opinionated server required)
- Academic/research: analyzing scientific papers with equations and figures

## Who Uses It in Production
- 18.9K stars; from the HKUDS research group at Hong Kong University (same group behind DeepTutor, LightRAG)
- v1.2.10 released March 24, 2026; 17 releases showing consistent maintenance
- Library-first design — embedded in custom applications rather than deployed as a standalone service
- Best suited for teams with Python engineering capability who want fine-grained control

## Tech Stack
- Python (100%)
- Built on LightRAG (graph-based retrieval core)
- Pluggable parsers: MinerU, Docling, PaddleOCR
- VLM integration for image/chart understanding during query
- Hybrid retrieval: vector similarity + knowledge graph traversal

## How to Deploy
1. `pip install raganything` (basic) or `pip install raganything[all]` (all parsers)
2. For Office docs: install LibreOffice on the system
3. Configure LLM and embedding model endpoints (OpenAI-compatible API)
4. Use `from raganything import RAGAnything` in your Python app
5. Optional: enable GPU acceleration for MinerU/PaddleOCR parsers

## Deploy Requirements
- **Min RAM:** 4 GB (8 GB+ recommended for large corpora or GPU parsing)
- **Min CPU:** Any modern CPU; GPU optional but beneficial for VLM
- **Storage:** Proportional to document corpus; knowledge graph stored locally
- **External deps:** LibreOffice (optional, for .docx/.pptx); GPU optional; LLM API
- **Estimated cost:** $0 self-hosted (library) + LLM API costs; GPU optional

## Security Assessment
- **Scorecard:** ~6/10 (MIT license, academic project, no enterprise security team)
- **Known CVEs:** None at time of profiling
- **Signed releases:** PyPI releases; no binary signing
- **Branch protection:** Standard GitHub
- **Dependency pinning:** requirements.txt with pinned versions
- **SBOM available:** No
- **Notes:** Academic-origin project; security practices follow research-software norms rather than enterprise-software norms. All processing runs locally. Vet parser dependencies (MinerU, PaddleOCR) for supply chain risk separately.

## Limitations & Gotchas
- Building the knowledge graph is computationally intensive for large document sets
- VLM image understanding quality depends on the model you configure — cheap models degrade table/chart accuracy
- Parser plugin quality varies — MinerU is best but heavier; PaddleOCR is lighter but less accurate on complex layouts
- No web UI or API server included — pure Python library
- Requires external LLM API; no bundled model

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| RAGFlow | Open Source | Full-stack server with UI; heavier; more enterprise-oriented |
| LlamaIndex | Open Source | Broader framework; text-dominant; less multimodal-native |
| Haystack | Open Source | Pipeline-first; good for text; multimodal is add-on |
| Unstructured.io | Open Source + Commercial | Parser-focused; less retrieval logic |
| LightRAG | Open Source | Graph-RAG base that RAG-Anything extends |

## Learning Value
- **Architecture patterns:** Multimodal knowledge graph construction — how to unify text + image + table + equation entities in one graph
- **Interesting techniques:** Adaptive chunking by content type within the same document; VLM-in-the-loop retrieval for image queries
- **Reusable components:** The parser abstraction layer; the LightRAG graph retrieval integration

## Links
- Docs: https://github.com/HKUDS/RAG-Anything#readme
- Related: https://github.com/HKUDS/LightRAG (base framework)
- PyPI: https://pypi.org/project/raganything
