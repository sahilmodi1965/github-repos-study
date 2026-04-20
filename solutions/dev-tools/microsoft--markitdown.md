---
name: "MarkItDown"
repo: "microsoft/markitdown"
url: "https://github.com/microsoft/markitdown"
category: "dev-tools"
stars: 113000
license: "MIT"
language: "Python"
last_profiled: "2026-04-20"
production_ready: true
security_score: 7  # Microsoft-backed, active maintenance, no known CVEs
deploy_complexity: "easy"
---

## What It Does
MarkItDown is a lightweight Python utility that converts virtually any document format (PDF, Word, Excel, PowerPoint, images, audio, HTML, CSV, JSON, EPUB, ZIP) into Markdown optimized for LLM ingestion. It preserves structural elements like headings, lists, and tables while stripping visual cruft, making it the go-to first step in any document AI pipeline.

## Use Cases
- Building document ingestion pipelines for RAG systems (PDFs, Word docs → Markdown chunks)
- Preprocessing office documents before sending to LLMs for summarization or Q&A
- Converting mixed-format file archives into a unified text corpus
- Feeding structured data (Excel, CSV) to agents in token-efficient Markdown tables
- MCP server mode: exposing file conversion as a tool for Claude Desktop / agents

## Who Uses It in Production
- Microsoft internal tooling (built by Microsoft AutoGen team)
- Widely adopted in the AutoGen and LangChain community for document preprocessing
- 113K+ GitHub stars indicates broad adoption across AI engineering teams

## Tech Stack
- Python 3.10+
- Pluggable architecture: `mammoth` (DOCX), `pdfminer.six` (PDF), `pillow` + OCR (images), `pydub`/`speech_recognition` (audio)
- Optional Azure Document Intelligence integration for high-fidelity PDF extraction
- MCP server via `mcp` package for Claude Desktop integration
- New `markitdown-ocr` plugin: LLM vision-powered image text extraction (no extra ML libs needed)

## How to Deploy
1. `pip install markitdown` (bare install — common formats only)
2. `pip install 'markitdown[all]'` (all format support including audio/image OCR)
3. CLI: `markitdown path/to/file.pdf > output.md`
4. Python API: `from markitdown import MarkItDown; md = MarkItDown(); result = md.convert("file.pdf")`
5. MCP server: `markitdown-mcp` — register in Claude Desktop config for in-agent file conversion

## Deploy Requirements
- **Min RAM:** 512 MB (2 GB+ recommended for audio/image OCR)
- **Min CPU:** 1 vCPU
- **Storage:** Minimal (<50 MB installed); temp space for large files
- **External deps:** Azure Document Intelligence (optional, for premium PDF); OpenAI API (optional, LLM-powered image descriptions)
- **Estimated cost:** Free self-hosted; Azure DI ~$0.001/page if used

## Security Assessment
- **Scorecard:** ~7/10 (estimated; Microsoft project with branch protection and CI)
- **Known CVEs:** None as of 2026-04-13
- **Signed releases:** Yes (PyPI releases via Microsoft CI)
- **Branch protection:** Yes (Microsoft org enforces code review)
- **Dependency pinning:** Partial (optional deps are version-ranged)
- **SBOM available:** Not published separately
- **Notes:** Low attack surface — pure Python file parsing. No network calls unless Azure DI or LLM image description is enabled. Be cautious with untrusted input files (malformed PDFs, ZIP bombs).

## Limitations & Gotchas
- Complex PDF layouts (multi-column, dense tables) degrade gracefully but aren't perfect — Azure DI mode is much better
- Audio transcription requires a local speech model or network call — not fully offline
- Image OCR quality depends on the underlying engine (Tesseract by default)
- No streaming — large files are fully loaded into memory
- Output Markdown fidelity varies by source format; always review before chunking for RAG

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Docling (IBM) | Open Source | Heavier, better table extraction, slower |
| Unstructured.io | Open Source / Cloud | More enterprise features, paid cloud tier |
| LlamaParse | Commercial | Higher accuracy PDFs, $0.003/page |
| Apache Tika | Open Source | Java-based, older but battle-tested |
| PyMuPDF | Open Source | PDF-only, faster, lower-level API |

## Learning Value
- **Architecture patterns:** Plugin-based format registry — clean extensibility pattern for adding new file types
- **Interesting techniques:** Format sniffing by MIME type + extension, unified result schema across all converters
- **Reusable components:** Individual format converters are usable standalone; MCP server pattern shows how to wrap a CLI tool as an agent tool

## Links
- Docs: https://github.com/microsoft/markitdown#readme
- Discord/Community: Microsoft AutoGen Discord
- Blog/Changelog: https://github.com/microsoft/markitdown/releases
- **Enriched 2026-04-20:** 113K stars (was 106K); new `markitdown-ocr` plugin added; latest release v0.1.5 (2026-02-20)
