---
name: "Chandra OCR"
repo: "datalab-to/chandra"
url: "https://github.com/datalab-to/chandra"
category: "ai-ocr"
stars: 6958
license: "Apache-2.0"
language: "Python"
last_profiled: "2026-03-28"
production_ready: true
security_score: "N/A — not in OpenSSF Scorecard DB"
deploy_complexity: "moderate"
---

## What It Does
Vision-language model for OCR that converts images and PDFs into structured outputs (HTML, Markdown, JSON) while preserving full document layout. Handles complex tables, forms with checkboxes, handwriting, mathematical expressions, and 90+ languages. Scores 85.9% accuracy on olmOCR benchmark vs competitors in the 60-70% range.

## Use Cases
- **Document digitization:** Convert scanned documents to structured data
- **Form processing:** Extract data from forms with checkboxes, signatures
- **Multilingual OCR:** Process documents in 90+ languages
- **Table extraction:** Complex tables → structured HTML/JSON
- **Handwriting recognition:** Convert handwritten notes to text
- **Invoice/receipt processing:** Structured extraction for accounting

## Who Uses It in Production
- Growing adoption, 6.9K stars
- Apache 2.0 license + free tier for startups/research encourages adoption

## Tech Stack
- Vision-language model (not traditional character-recognition OCR)
- HuggingFace Transformers for local inference
- vLLM server for production deployment
- ~1.44 pages/second on H100 GPU

## How to Deploy
1. `pip install chandra-ocr` or use HuggingFace Transformers
2. For production: deploy vLLM server with model
3. API interface for batch processing

## Deploy Requirements
- **Min RAM:** 8+ GB (GPU VRAM)
- **Min CPU:** GPU recommended (H100 for production throughput)
- **Storage:** Model weights (several GB)
- **External deps:** CUDA-capable GPU
- **Estimated cost:** Self-hosted GPU or cloud GPU instances. Free API tier for startups.

## Accuracy Benchmarks (ELO-based, 5,005 documents)
| Model | ELO Score |
|-------|-----------|
| Chandra+ (Accurate) | 1798 |
| Chandra (Balanced) | 1638 |
| Chandra Small (Fast) | 1528 |
| dots.ocr | 1489 |
| olmOCR 2 | 1387 |
| DeepSeek OCR | 1336 |

**Multilingual:** 72.7% avg across 90 languages vs Gemini 2.5 Flash at 60.8%. Massive gains on South Asian scripts (Bengali +27.2, Malayalam +46.2, Telugu +39.1 points).

## Best/Worst Document Types
- **Excels at:** Complex tables with nested cells, handwriting (tested on Ramanujan's 1913 letter), forms with checkboxes, multi-column layouts, math/scientific notation, low-quality scans, South Asian scripts
- **Tested categories:** Finance, Healthcare, Invoices, Legal, Research Papers, Textbooks, Forms
- **Weakness:** Outperformed by dot-ocr in layout mode for some use cases

## Security Assessment
- **Scorecard:** N/A (not in OpenSSF DB)
- **Security policy:** None
- **Branch protection:** No
- **CI/CD:** Yes (2 workflows)
- **Signed releases:** No
- **Contributors:** ~3 (very small team)
- **Last commit:** 2026-03-18
- **Open issues:** 32
- **Dependency pinning:** Yes (uv.lock)

## License Warning
- **Code:** Apache 2.0
- **Model weights:** Modified OpenRAIL-M — free for research, personal use, and startups under $2M funding/revenue. **Cannot be used competitively with Datalab's API. Commercial license required for larger organizations.** This is a recurring complaint in the community.

## Limitations & Gotchas
- Requires GPU for practical speeds
- Model download is large
- Not real-time for high-volume batch processing on consumer hardware
- Layout preservation quality varies with document complexity
- **Model license is restrictive for commercial use** — not truly "open" for larger companies
- Company context: Datalab is small NYC team, 7-figure ARR, ~7x growth in 2025

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| Tesseract | Open Source | Free but much lower accuracy, no layout understanding |
| Google Document AI | Commercial | Higher accuracy at scale, but costs per page |
| AWS Textract | Commercial | Good table extraction, pay per page |
| Azure Document Intelligence | Commercial | Microsoft's offering, enterprise-focused |
| PaddleOCR | Open Source | Good for Asian languages, less layout preservation |
| Marker (datalab) | Open Source | Same team, focused on PDF → Markdown conversion |

## Learning Value
- **Architecture patterns:** Vision-language model for document understanding (vs traditional OCR pipelines)
- **Interesting techniques:** Holistic layout understanding rather than character-by-character recognition
- **Reusable components:** The structured output approach (images → HTML/JSON preserving spatial relationships)

## Links
- Repo: https://github.com/datalab-to/chandra
