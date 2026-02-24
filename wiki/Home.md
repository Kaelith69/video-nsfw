<div align="center">

<!-- Wiki Home Hero Banner -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 140" width="820" height="140">
  <defs>
    <linearGradient id="homeBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="homeAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <filter id="homeGlow">
      <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>
  <rect width="820" height="140" fill="url(#homeBg)" rx="10"/>
  <rect x="1" y="1" width="818" height="138" fill="none" stroke="#7C3AED" stroke-width="1" rx="10" opacity="0.5"/>
  <text x="410" y="58" text-anchor="middle" fill="white" font-size="32" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#homeGlow)">video-nsfw Wiki</text>
  <text x="410" y="88" text-anchor="middle" fill="#a5b4fc" font-size="14"
        font-family="'Segoe UI', Arial, sans-serif" letter-spacing="2">
    Complete Developer Documentation
  </text>
  <rect x="160" y="102" width="500" height="2" fill="url(#homeAccent)" rx="1" opacity="0.7"/>
  <text x="410" y="122" text-anchor="middle" fill="#8b8fa8" font-size="11"
        font-family="monospace">PyTorch · Transformers · OpenCV · ViT · CUDA</text>
</svg>

</div>

# Welcome to the video-nsfw Wiki

This wiki provides complete technical documentation for **video-nsfw** — an AI-powered video content moderation library built on Vision Transformers, PyTorch, and OpenCV.

---

## 📚 Documentation Index

| Page | Description |
|---|---|
| **[Home](Home)** *(this page)* | Project overview, quick start, and navigation |
| **[Architecture](Architecture)** | System design, component breakdown, and internal structure |
| **[Installation](Installation)** | Detailed setup guide for all platforms |
| **[Usage](Usage)** | CLI reference, Python API, and integration patterns |
| **[Privacy](Privacy)** | Data handling, security model, and compliance notes |
| **[Contributing](Contributing)** | Development workflow, code standards, and PR process |
| **[Troubleshooting](Troubleshooting)** | Common issues, debugging guide, and FAQ |
| **[Roadmap](Roadmap)** | Planned features, versioning, and contribution priorities |

---

## 🚀 Quick Start

```bash
# Clone and install
git clone https://github.com/Kaelith69/video-nsfw.git
cd video-nsfw
pip install -r requirements.txt

# Run on a video
python video_analyzer.py my_video.mp4
```

**Python API (3 lines):**

```python
from video_analyzer import VideoContentAnalyzer
analyzer = VideoContentAnalyzer()
results = analyzer.analyze_video("my_video.mp4")
```

---

## 🧠 What Is video-nsfw?

`video-nsfw` is a focused Python library that provides **NSFW content detection for video files**. It:

1. Samples `N` evenly-spaced frames from a video using OpenCV
2. Converts each frame to a PIL Image
3. Runs each image through a fine-tuned **Vision Transformer (ViT)** model (`Falconsai/nsfw_image_detection`) via HuggingFace Transformers
4. Returns per-frame classification results (`nsfw` / `normal`) with confidence scores
5. Optionally stops early on the first NSFW detection

The entire pipeline runs locally — no data leaves your machine.

---

## 🧩 Key Concepts

| Concept | Explanation |
|---|---|
| **Vision Transformer (ViT)** | A transformer-based image classifier that processes images as sequences of patches |
| **Frame Sampling** | Selecting a fixed number of representative frames from a video instead of processing every frame |
| **Confidence Score** | Softmax probability (0.0–1.0) indicating how strongly the model believes a frame is NSFW |
| **NSFW Threshold** | Minimum confidence required to flag a frame as NSFW (default: 0.5) |
| **Early Stop** | Halting analysis after the first NSFW detection to reduce latency |
| **Device Selection** | Automatic use of CUDA GPU when available, otherwise CPU |

---

## 🗂 Project Files

```
video-nsfw/
├── video_analyzer.py      # Core library: VideoContentAnalyzer class + CLI
├── requirements.txt       # Python dependency manifest
├── LICENSE                # MIT License
├── README.md              # Project readme with diagrams
└── wiki/                  # This documentation set
    ├── Home.md
    ├── Architecture.md
    ├── Installation.md
    ├── Usage.md
    ├── Privacy.md
    ├── Contributing.md
    ├── Troubleshooting.md
    └── Roadmap.md
```

---

## 💬 Getting Help

- **Bug reports / feature requests:** [Open an issue](https://github.com/Kaelith69/video-nsfw/issues)
- **Contributing:** See the [Contributing](Contributing) page
- **Troubleshooting:** See the [Troubleshooting](Troubleshooting) page
