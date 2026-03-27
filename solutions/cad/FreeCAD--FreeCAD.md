---
name: "FreeCAD"
repo: "FreeCAD/FreeCAD"
url: "https://github.com/FreeCAD/FreeCAD"
category: "cad"
stars: 29605
license: "LGPL-2.1"
language: "C++"
last_profiled: "2026-03-28"
production_ready: true
security_score: 6.8  # OpenSSF Scorecard (2026-03-27)
deploy_complexity: "trivial"
---

## What It Does
Free, open-source parametric 3D modeler for designing real-world objects. Parametric means designs are defined by adjustable parameters that propagate changes through the entire model. Supports full 2D-to-3D workflow: constrained 2D sketches → 3D solids → production-quality technical drawings.

## Use Cases
- **Mechanical engineering:** Part and assembly design
- **3D printing:** Design models for FDM/SLA printers
- **Architecture (BIM):** Building information modeling
- **CAM:** Computer-aided manufacturing toolpaths
- **Education:** Teaching CAD without commercial license costs
- **Hobbyist/maker projects**

## Who Uses It in Production
- 14 years of active development (since 2012)
- FreeCAD Project Association manages funding
- Used by engineers, educators, makers worldwide
- Cross-platform: Windows, macOS, Linux

## Tech Stack
- C++ core with four pillars: OpenCASCADE (geometry kernel), Coin3D (3D viz), Qt (GUI), Python (scripting)
- Modular "workbench" architecture: Part Design, FEM, Architecture/BIM, CAM, etc.
- Full Python scripting API for automation

## How to Deploy
1. Download from freecad.org or package manager
2. Install and run — no server, no account, no setup

## Deploy Requirements
- **Min RAM:** 4 GB
- **Min CPU:** Any modern CPU
- **Storage:** ~500 MB
- **External deps:** None
- **Estimated cost:** Free

## OpenSSF Scorecard Details (6.8/10, scored 2026-03-27)
| Check | Score |
|-------|-------|
| Maintained | 10/10 |
| Code-Review | 10/10 |
| CI-Tests | 10/10 |
| Security-Policy | 10/10 |
| Dangerous-Workflow | 10/10 |
| Vulnerabilities | 10/10 |
| SAST | 9/10 |
| Contributors | 10/10 |
| Pinned-Dependencies | 7/10 |
| Branch-Protection | 1/10 |
| Signed-Releases | 0/10 |
| Token-Permissions | 0/10 |
| Fuzzing | 0/10 |

## Release Status
- **FreeCAD 1.0** released Nov 19, 2024 (after 20 years of development)
- **FreeCAD 1.1** released Jul 2025 (1,700+ changes)
- Topological Naming fix: **substantially complete for Sketcher + PartDesign** in 1.0/1.1. Ondsel completed Phase 2 and declared it "officially history." But Ondsel shut down — continued progress depends on volunteers.
- Assembly workbench: graduated from add-on to built-in in 1.0, improved in 1.1, but still not competitive with SolidWorks for large-scale industrial use

## Limitations & Gotchas
- Steeper learning curve than commercial CAD tools
- Topological naming: mostly fixed for PartDesign but other workbenches may still have edge cases
- Assembly workbench: functional but ecosystem is fragmented (A2plus, Assembly3, Assembly4 still exist)
- UI can feel rough compared to commercial alternatives
- **Ondsel (company driving TNP fix) shut down** — maintenance now fully community-driven

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| SolidWorks | Commercial ($$$) | Industry standard, expensive |
| Fusion 360 | Commercial | Free for personal use, cloud-dependent |
| OnShape | Commercial | Browser-based, subscription model |
| OpenSCAD | Open Source | Code-based modeling (no GUI sketching) |
| Blender | Open Source | More for artistic/mesh modeling than engineering |

## Learning Value
- **Architecture patterns:** Modular workbench plugin architecture, parametric constraint solver
- **Interesting techniques:** How OpenCASCADE BREP kernel handles parametric modeling
- **Reusable components:** The Python scripting API pattern for exposing C++ functionality

## Links
- Docs: https://wiki.freecad.org
- Community: Forum, Discord, Reddit
- Download: https://www.freecad.org
