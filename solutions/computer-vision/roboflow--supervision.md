---
name: "Supervision"
repo: "roboflow/supervision"
url: "https://github.com/roboflow/supervision"
category: "computer-vision"
stars: 37700
license: "MIT"
language: "Python"
last_profiled: "2026-04-06"
production_ready: true
security_score: 7
deploy_complexity: "easy"
---

## What It Does
Model-agnostic Python toolkit that handles everything after the raw model inference step in computer vision: annotation visualization, object tracking, zone analysis, dataset management, and format conversion. Works with any detection/segmentation model (YOLO, SAM, DETIC, Grounding DINO, etc.) and converts results into a unified `Detections` format for downstream processing.

## Use Cases
- Video surveillance: count objects in zones, track movement across frames
- Traffic monitoring: vehicle counting, speed estimation, lane analysis
- Sports analytics: player tracking, ball detection, event detection
- Retail: customer flow analysis, shelf monitoring, queue counting
- Industrial QA: defect detection pipeline with annotated output
- Dataset prep: convert between YOLO / COCO / Pascal VOC formats, merge and split datasets

## Who Uses It in Production
- Maintained by Roboflow (the largest vision AI platform company)
- Widely used in academic + startup computer vision projects
- 37.7K stars; integrates with Roboflow Inference (cloud) and local models
- Used in traffic, sports, and retail CV production deployments

## Tech Stack
- Python library (pip installable)
- Integrates with: Ultralytics (YOLOv8–v12), HuggingFace Transformers, MMDetection, Roboflow Inference
- Core abstractions: `Detections`, `Annotators`, `ByteTrack`, `VideoInfo`, `PolygonZone`
- No mandatory GPU — CPU inference supported for lightweight models

## How to Deploy
1. `pip install supervision`
2. Load any detection model (e.g., Ultralytics YOLO): `model = YOLO("yolov8n.pt")`
3. Run inference and wrap with Supervision: `detections = sv.Detections.from_ultralytics(result)`
4. Annotate and visualize: `annotated = annotator.annotate(frame, detections)`
5. For video: use `sv.VideoSink` to write annotated output video
6. For zones: define `sv.PolygonZone` and count detections per frame

## Deploy Requirements
- **Min RAM:** 512 MB (CPU inference); 4 GB+ for GPU-accelerated models
- **Min CPU:** Any modern CPU; GPU optional
- **Storage:** ~50 MB for library; model weights vary (6 MB–600 MB)
- **External deps:** Detection model of choice (YOLO, SAM, etc.)
- **Estimated cost:** $0 for local inference; Roboflow Inference cloud has a free tier

## Security Assessment
- **Scorecard:** ~7/10
- **Known CVEs:** None known at time of profiling
- **Signed releases:** PyPI releases (no explicit signing)
- **Branch protection:** Yes
- **Dependency pinning:** Yes (requirements files)
- **SBOM available:** Partial via pip
- **Notes:** Library-only — no network exposure by default. Security posture depends on the model source and any upstream data pipelines.

## Limitations & Gotchas
- Primarily a post-processing library — does not provide model training or fine-tuning
- Tracking algorithms (ByteTrack) can drift in dense crowd scenarios
- Zone analysis requires manual polygon definition per deployment environment
- Real-time performance depends heavily on underlying model speed
- No built-in model serving — pair with FastAPI or Roboflow Inference for APIs

## Alternatives & Competitors
| Solution | Type | Difference |
|----------|------|------------|
| OpenCV | Open Source | Lower-level, more flexibility, more boilerplate |
| Detectron2 | Open Source | Facebook's framework, training-focused |
| Ultralytics | Open Source | Model-first (YOLO family), supervision is a complement not competitor |
| Roboflow Inference | Commercial | Hosted serving layer; supervision is the local toolkit counterpart |

## Learning Value
- **Architecture patterns:** Unified `Detections` dataclass — clean abstraction for heterogeneous model outputs
- **Interesting techniques:** ByteTrack implementation for real-time multi-object tracking; PolygonZone hit-testing for spatial analytics
- **Reusable components:** The annotator system (bounding boxes, labels, masks, heatmaps); the dataset conversion utilities

## Links
- Docs: https://supervision.roboflow.com
- Discord: https://discord.gg/roboflow
- Blog: https://blog.roboflow.com
