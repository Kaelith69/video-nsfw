# Roadmap

This page tracks the planned evolution of `video-nsfw` — from its current minimal core to a fully-featured content moderation toolkit.

---

## Current State (v1.0.0)

The initial release provides a clean, focused Python library with:

- ✅ `VideoContentAnalyzer` class with `analyze_video()` and `analyze_frame()` methods
- ✅ GPU/CPU automatic device selection
- ✅ Configurable frame sampling count
- ✅ Configurable NSFW confidence threshold
- ✅ Early-stop on first NSFW detection
- ✅ Rich per-frame result dictionary
- ✅ CLI entry point
- ✅ Safe resource handling (`try/finally`)

---

## Planned Features

### v1.1 — Usability & Integration

| Feature | Priority | Description |
|---|---|---|
| **Batch video processing** | High | Accept a list of paths and return results for all videos |
| **Progress callback** | Medium | Optional callback function called after each frame analysis |
| **JSON output for CLI** | Medium | `--json` flag to output results as JSON instead of text |
| **Configurable CLI flags** | Medium | Expose `--num-frames`, `--threshold`, `--no-stop` as CLI arguments |

**Example (batch):**
```python
results_map = analyzer.analyze_videos(
    ["video1.mp4", "video2.mp4", "video3.mp4"],
    num_frames=8,
)
```

**Example (progress callback):**
```python
def on_frame(frame_result):
    print(f"Frame {frame_result['frame_number']}: {frame_result['prediction']}")

analyzer.analyze_video("video.mp4", on_frame=on_frame)
```

---

### v1.2 — Accuracy & Sampling

| Feature | Priority | Description |
|---|---|---|
| **Scene-change-aware sampling** | High | Use scene detection to sample at scene boundaries instead of fixed intervals |
| **Confidence calibration** | Medium | Post-hoc calibration (Platt scaling / temperature scaling) to improve probability estimates |
| **Alternative model support** | Medium | Easy swap to CLIP-based classifiers or multi-label models |
| **Ensemble scoring** | Low | Run multiple models and aggregate scores |

**Scene-change sampling** would significantly improve detection accuracy for videos where NSFW content appears in a single scene, which fixed-interval sampling might miss.

---

### v1.3 — Performance

| Feature | Priority | Description |
|---|---|---|
| **Async/concurrent frame processing** | High | Process multiple frames in parallel using `asyncio` or `ThreadPoolExecutor` |
| **Frame batching** | High | Send multiple frames to the model in a single forward pass to utilise GPU throughput |
| **FP16 inference** | Medium | Half-precision inference for ~2× GPU speedup with minimal accuracy loss |
| **TorchScript / ONNX export** | Low | Export the model for deployment in non-Python environments |

**Frame batching** example (planned API):
```python
analyzer = VideoContentAnalyzer(batch_size=8)  # Process 8 frames per GPU pass
```

---

### v1.4 — Deployment & Integration

| Feature | Priority | Description |
|---|---|---|
| **FastAPI / REST wrapper** | High | HTTP API for integrating with web services |
| **Docker image** | High | Official Docker image with model pre-cached |
| **Webhook support** | Medium | POST results to a URL on detection |
| **Message queue integration** | Low | Consume video paths from RabbitMQ/Kafka |

**FastAPI example (planned):**
```bash
uvicorn video_nsfw_api:app --host 0.0.0.0 --port 8080

# POST /analyze
curl -F "video=@clip.mp4" http://localhost:8080/analyze
```

---

### v2.0 — Multi-Modal Moderation

| Feature | Priority | Description |
|---|---|---|
| **Audio moderation** | Medium | Transcribe audio and classify text for harmful speech |
| **Text overlay detection** | Low | OCR on frames to detect harmful text in video |
| **Temporal context** | Low | Use consecutive frame sequences (video transformer) for better accuracy |
| **Multi-label classification** | Low | Distinguish sub-categories (nudity, violence, etc.) |

---

## Version History

| Version | Date | Highlights |
|---|---|---|
| `1.0.0` | 2025 | Initial release — single class, ViT inference, GPU/CPU, CLI |

---

## Contributing to the Roadmap

Have a feature idea? Open a GitHub issue with:

1. The feature description
2. Your use case
3. Any relevant prior art or references

High-impact, well-scoped contributions are prioritised. See [Contributing](Contributing) for the PR process.

---

## Versioning Policy

This project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** — Breaking API changes
- **MINOR** — New backwards-compatible features
- **PATCH** — Bug fixes and performance improvements

The public API consists of:
- `VideoContentAnalyzer.__init__(model_name)`
- `VideoContentAnalyzer.analyze_video(video_path, num_frames, stop_on_nsfw, nsfw_threshold)`
- `VideoContentAnalyzer.analyze_frame(image)`
- The result dict schema returned by `analyze_video()`
