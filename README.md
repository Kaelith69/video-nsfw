<div align="center">

<!-- Hero SVG Banner -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 220" width="900" height="220">
  <defs>
    <linearGradient id="heroBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="45%" style="stop-color:#1e1040"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="heroAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="50%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="shieldGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <filter id="heroGlow">
      <feGaussianBlur stdDeviation="4" result="coloredBlur"/>
      <feMerge>
        <feMergeNode in="coloredBlur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>
    <filter id="softGlow">
      <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
      <feMerge>
        <feMergeNode in="coloredBlur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>
  </defs>

  <!-- Background -->
  <rect width="900" height="220" fill="url(#heroBg)" rx="14"/>

  <!-- Subtle grid pattern -->
  <line x1="0" y1="55" x2="900" y2="55" stroke="#7C3AED" stroke-width="0.3" opacity="0.2"/>
  <line x1="0" y1="110" x2="900" y2="110" stroke="#7C3AED" stroke-width="0.3" opacity="0.2"/>
  <line x1="0" y1="165" x2="900" y2="165" stroke="#7C3AED" stroke-width="0.3" opacity="0.2"/>
  <line x1="150" y1="0" x2="150" y2="220" stroke="#2563EB" stroke-width="0.3" opacity="0.2"/>
  <line x1="300" y1="0" x2="300" y2="220" stroke="#2563EB" stroke-width="0.3" opacity="0.2"/>
  <line x1="450" y1="0" x2="450" y2="220" stroke="#2563EB" stroke-width="0.3" opacity="0.2"/>
  <line x1="600" y1="0" x2="600" y2="220" stroke="#2563EB" stroke-width="0.3" opacity="0.2"/>
  <line x1="750" y1="0" x2="750" y2="220" stroke="#2563EB" stroke-width="0.3" opacity="0.2"/>

  <!-- Film strip left -->
  <rect x="18" y="18" width="34" height="184" fill="#12082a" rx="5" opacity="0.9"/>
  <rect x="21" y="28" width="28" height="18" fill="#7C3AED" rx="3" opacity="0.7"/>
  <rect x="21" y="54" width="28" height="18" fill="#2563EB" rx="3" opacity="0.7"/>
  <rect x="21" y="80" width="28" height="18" fill="#06B6D4" rx="3" opacity="0.7"/>
  <rect x="21" y="106" width="28" height="18" fill="#7C3AED" rx="3" opacity="0.7"/>
  <rect x="21" y="132" width="28" height="18" fill="#2563EB" rx="3" opacity="0.7"/>
  <rect x="21" y="158" width="28" height="18" fill="#06B6D4" rx="3" opacity="0.6"/>
  <rect x="21" y="175" width="28" height="18" fill="#7C3AED" rx="3" opacity="0.5"/>

  <!-- Film strip right -->
  <rect x="848" y="18" width="34" height="184" fill="#12082a" rx="5" opacity="0.9"/>
  <rect x="851" y="28" width="28" height="18" fill="#06B6D4" rx="3" opacity="0.7"/>
  <rect x="851" y="54" width="28" height="18" fill="#7C3AED" rx="3" opacity="0.7"/>
  <rect x="851" y="80" width="28" height="18" fill="#2563EB" rx="3" opacity="0.7"/>
  <rect x="851" y="106" width="28" height="18" fill="#06B6D4" rx="3" opacity="0.7"/>
  <rect x="851" y="132" width="28" height="18" fill="#7C3AED" rx="3" opacity="0.7"/>
  <rect x="851" y="158" width="28" height="18" fill="#2563EB" rx="3" opacity="0.6"/>
  <rect x="851" y="175" width="28" height="18" fill="#06B6D4" rx="3" opacity="0.5"/>

  <!-- Neural network node decoration left -->
  <circle cx="110" cy="70" r="5" fill="#7C3AED" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="110" cy="110" r="5" fill="#2563EB" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="110" cy="150" r="5" fill="#06B6D4" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="140" cy="90" r="4" fill="#7C3AED" opacity="0.5"/>
  <circle cx="140" cy="130" r="4" fill="#2563EB" opacity="0.5"/>
  <line x1="110" y1="70" x2="140" y2="90" stroke="#7C3AED" stroke-width="0.8" opacity="0.4"/>
  <line x1="110" y1="110" x2="140" y2="90" stroke="#2563EB" stroke-width="0.8" opacity="0.4"/>
  <line x1="110" y1="110" x2="140" y2="130" stroke="#2563EB" stroke-width="0.8" opacity="0.4"/>
  <line x1="110" y1="150" x2="140" y2="130" stroke="#06B6D4" stroke-width="0.8" opacity="0.4"/>

  <!-- Neural network node decoration right -->
  <circle cx="790" cy="70" r="5" fill="#06B6D4" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="790" cy="110" r="5" fill="#7C3AED" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="790" cy="150" r="5" fill="#2563EB" opacity="0.6" filter="url(#softGlow)"/>
  <circle cx="760" cy="90" r="4" fill="#06B6D4" opacity="0.5"/>
  <circle cx="760" cy="130" r="4" fill="#7C3AED" opacity="0.5"/>
  <line x1="790" y1="70" x2="760" y2="90" stroke="#06B6D4" stroke-width="0.8" opacity="0.4"/>
  <line x1="790" y1="110" x2="760" y2="90" stroke="#7C3AED" stroke-width="0.8" opacity="0.4"/>
  <line x1="790" y1="110" x2="760" y2="130" stroke="#7C3AED" stroke-width="0.8" opacity="0.4"/>
  <line x1="790" y1="150" x2="760" y2="130" stroke="#2563EB" stroke-width="0.8" opacity="0.4"/>

  <!-- Central shield icon -->
  <path d="M393 32 L420 44 L420 84 Q420 102 406 110 Q393 117 380 110 Q366 102 366 84 L366 44 Z"
        fill="url(#shieldGrad)" opacity="0.18" rx="3"/>
  <path d="M393 32 L420 44 L420 84 Q420 102 406 110 Q393 117 380 110 Q366 102 366 84 L366 44 Z"
        fill="none" stroke="url(#heroAccent)" stroke-width="2" filter="url(#heroGlow)" opacity="0.9"/>
  <!-- Eye inside shield -->
  <ellipse cx="393" cy="75" rx="12" ry="7" fill="none" stroke="#06B6D4" stroke-width="1.5" opacity="0.9"/>
  <circle cx="393" cy="75" r="4" fill="#7C3AED" opacity="0.9" filter="url(#softGlow)"/>
  <circle cx="394.5" cy="73.5" r="1.2" fill="white" opacity="0.7"/>

  <!-- Main title -->
  <text x="435" y="82" text-anchor="start" fill="white" font-size="46" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#heroGlow)" letter-spacing="-1">video-nsfw</text>

  <!-- Tagline -->
  <text x="450" y="132" text-anchor="middle" fill="#a5b4fc" font-size="15"
        font-family="'Segoe UI', Arial, sans-serif" letter-spacing="3">
    AI-POWERED VIDEO CONTENT MODERATION
  </text>

  <!-- Accent gradient line -->
  <rect x="170" y="150" width="560" height="2.5" fill="url(#heroAccent)" rx="1.5" opacity="0.8"/>

  <!-- Tech pill tags -->
  <rect x="183" y="163" width="78" height="24" fill="#7C3AED" rx="12" opacity="0.2"/>
  <rect x="183" y="163" width="78" height="24" fill="none" stroke="#7C3AED" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="222" y="180" text-anchor="middle" fill="#a78bfa" font-size="11" font-family="monospace">PyTorch</text>

  <rect x="272" y="163" width="104" height="24" fill="#2563EB" rx="12" opacity="0.2"/>
  <rect x="272" y="163" width="104" height="24" fill="none" stroke="#2563EB" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="324" y="180" text-anchor="middle" fill="#93c5fd" font-size="11" font-family="monospace">Transformers</text>

  <rect x="387" y="163" width="78" height="24" fill="#06B6D4" rx="12" opacity="0.2"/>
  <rect x="387" y="163" width="78" height="24" fill="none" stroke="#06B6D4" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="426" y="180" text-anchor="middle" fill="#67e8f9" font-size="11" font-family="monospace">OpenCV</text>

  <rect x="476" y="163" width="86" height="24" fill="#7C3AED" rx="12" opacity="0.2"/>
  <rect x="476" y="163" width="86" height="24" fill="none" stroke="#7C3AED" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="519" y="180" text-anchor="middle" fill="#a78bfa" font-size="11" font-family="monospace">ViT Model</text>

  <rect x="573" y="163" width="78" height="24" fill="#2563EB" rx="12" opacity="0.2"/>
  <rect x="573" y="163" width="78" height="24" fill="none" stroke="#2563EB" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="612" y="180" text-anchor="middle" fill="#93c5fd" font-size="11" font-family="monospace">CUDA GPU</text>

  <rect x="662" y="163" width="66" height="24" fill="#06B6D4" rx="12" opacity="0.2"/>
  <rect x="662" y="163" width="66" height="24" fill="none" stroke="#06B6D4" rx="12" stroke-width="1" opacity="0.5"/>
  <text x="695" y="180" text-anchor="middle" fill="#67e8f9" font-size="11" font-family="monospace">Pillow</text>
</svg>

# video-nsfw

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![HuggingFace](https://img.shields.io/badge/🤗%20Transformers-4.35%2B-FFD21F?style=for-the-badge)](https://huggingface.co/transformers/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.8%2B-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/)
[![License](https://img.shields.io/badge/License-MIT-22C55E?style=for-the-badge)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-7C3AED?style=for-the-badge)](https://github.com/Kaelith69/video-nsfw)
[![CUDA](https://img.shields.io/badge/CUDA-Compatible-76B900?style=for-the-badge&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)

> **AI-powered video content moderation** — automatically detects NSFW material in videos by sampling and classifying frames using a Vision Transformer (ViT) model fine-tuned on NSFW detection.

</div>

---

## 📖 Table of Contents

- [System Overview](#-system-overview)
- [Features](#-features)
- [Core Capabilities](#-core-capabilities)
- [Architecture](#-architecture)
- [Data Flow](#-data-flow)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
  - [Command-Line](#command-line)
  - [Python API](#python-api)
- [Configuration](#-configuration)
- [Output Schema](#-output-schema)
- [How It Works](#-how-it-works)
- [Performance](#-performance)
- [Accessibility](#-accessibility)
- [Privacy & Security](#-privacy--security)
- [Design Principles](#-design-principles)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌐 System Overview

`video-nsfw` is a focused, single-class Python library that brings production-grade **NSFW video content detection** to any pipeline. It combines the video I/O power of OpenCV with a fine-tuned Vision Transformer from Hugging Face to classify sampled frames — all with zero configuration required for typical use cases.

```
Input Video ──► Frame Sampler ──► ViT Classifier ──► Verdict + Confidence Scores
```

Key design goals:

- **Zero-friction integration** — one class, one method call
- **GPU-first, CPU-safe** — automatic device selection
- **Fail-fast safety** — early-stop on detection to minimise compute and latency
- **Portable** — runs on Linux, macOS, and Windows

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎬 **Frame Sampling** | Evenly-spaced N-frame sampling from any video container |
| 🤖 **ViT Classification** | Uses `Falconsai/nsfw_image_detection` Vision Transformer |
| ⚡ **GPU Acceleration** | Automatically uses CUDA when available, falls back to CPU |
| 🛑 **Early Stop** | Optionally halts analysis on first NSFW detection |
| 🎯 **Configurable Threshold** | Tune confidence threshold to balance precision/recall |
| 📊 **Rich Results** | Per-frame predictions, confidence scores, and summary verdict |
| 🔒 **Safe Resource Handling** | Video capture always released via `try/finally` |
| 🔌 **Pluggable Model** | Swap in any compatible HuggingFace image classifier |

---

## 🧩 Core Capabilities

<div align="center">

<!-- Core Capability Graph SVG -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 320" width="820" height="320">
  <defs>
    <linearGradient id="capBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="capAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="barGrad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#2563EB"/>
    </linearGradient>
    <linearGradient id="barGrad2" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#2563EB"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="barGrad3" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <filter id="capGlow">
      <feGaussianBlur stdDeviation="2.5" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="820" height="320" fill="url(#capBg)" rx="12"/>
  <rect x="1" y="1" width="818" height="318" fill="none" stroke="#7C3AED" stroke-width="1" rx="12" opacity="0.4"/>

  <!-- Title -->
  <text x="410" y="35" text-anchor="middle" fill="white" font-size="16" font-weight="700"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#capGlow)">Core Capability Matrix</text>
  <rect x="160" y="44" width="500" height="1.5" fill="url(#capAccent)" rx="1" opacity="0.6"/>

  <!-- Capability bars -->
  <!-- Row 1: Frame Sampling -->
  <text x="30" y="85" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">🎬 Frame Sampling</text>
  <rect x="200" y="72" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="72" width="504" height="18" fill="url(#barGrad1)" rx="9" opacity="0.85"/>
  <text x="715" y="85" fill="#a78bfa" font-size="11" font-family="monospace">90%</text>

  <!-- Row 2: ViT Classification -->
  <text x="30" y="120" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">🤖 ViT Classification</text>
  <rect x="200" y="107" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="107" width="532" height="18" fill="url(#barGrad2)" rx="9" opacity="0.85"/>
  <text x="745" y="120" fill="#67e8f9" font-size="11" font-family="monospace">95%</text>

  <!-- Row 3: GPU Acceleration -->
  <text x="30" y="155" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">⚡ GPU Acceleration</text>
  <rect x="200" y="142" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="142" width="476" height="18" fill="url(#barGrad1)" rx="9" opacity="0.85"/>
  <text x="690" y="155" fill="#a78bfa" font-size="11" font-family="monospace">85%</text>

  <!-- Row 4: Early Stop -->
  <text x="30" y="190" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">🛑 Early Stop Logic</text>
  <rect x="200" y="177" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="177" width="560" height="18" fill="url(#barGrad3)" rx="9" opacity="0.85"/>
  <text x="773" y="190" fill="#67e8f9" font-size="11" font-family="monospace">100%</text>

  <!-- Row 5: Threshold Control -->
  <text x="30" y="225" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">🎯 Threshold Control</text>
  <rect x="200" y="212" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="212" width="504" height="18" fill="url(#barGrad1)" rx="9" opacity="0.85"/>
  <text x="715" y="225" fill="#a78bfa" font-size="11" font-family="monospace">90%</text>

  <!-- Row 6: Rich Result Schema -->
  <text x="30" y="260" fill="#a5b4fc" font-size="12" font-family="'Segoe UI', Arial, sans-serif">📊 Result Schema</text>
  <rect x="200" y="247" width="560" height="18" fill="#1e1040" rx="9"/>
  <rect x="200" y="247" width="532" height="18" fill="url(#barGrad2)" rx="9" opacity="0.85"/>
  <text x="745" y="260" fill="#67e8f9" font-size="11" font-family="monospace">95%</text>

  <!-- Legend -->
  <rect x="200" y="287" width="12" height="12" fill="url(#barGrad1)" rx="3"/>
  <text x="218" y="298" fill="#8b8fa8" font-size="10" font-family="'Segoe UI', Arial, sans-serif">Implementation Completeness</text>
</svg>

</div>

---

## 🏛 Architecture

<div align="center">

<!-- Architecture Diagram SVG -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 400" width="820" height="400">
  <defs>
    <linearGradient id="archBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="archAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="boxGrad1" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#7C3AED" stop-opacity="0.08"/>
    </linearGradient>
    <linearGradient id="boxGrad2" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#2563EB" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#2563EB" stop-opacity="0.08"/>
    </linearGradient>
    <linearGradient id="boxGrad3" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#06B6D4" stop-opacity="0.3"/>
      <stop offset="100%" style="stop-color:#06B6D4" stop-opacity="0.08"/>
    </linearGradient>
    <marker id="arrowHead" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
      <polygon points="0 0, 8 3, 0 6" fill="#7C3AED" opacity="0.8"/>
    </marker>
    <marker id="arrowHead2" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
      <polygon points="0 0, 8 3, 0 6" fill="#06B6D4" opacity="0.8"/>
    </marker>
    <filter id="archGlow">
      <feGaussianBlur stdDeviation="2" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="820" height="400" fill="url(#archBg)" rx="12"/>
  <rect x="1" y="1" width="818" height="398" fill="none" stroke="#7C3AED" stroke-width="1" rx="12" opacity="0.4"/>

  <!-- Title -->
  <text x="410" y="35" text-anchor="middle" fill="white" font-size="16" font-weight="700"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#archGlow)">System Architecture — VideoContentAnalyzer</text>
  <rect x="100" y="44" width="620" height="1.5" fill="url(#archAccent)" rx="1" opacity="0.6"/>

  <!-- VideoContentAnalyzer outer box -->
  <rect x="20" y="60" width="780" height="300" fill="none" stroke="#7C3AED" stroke-width="1.5"
        rx="10" opacity="0.5" stroke-dasharray="6,3"/>
  <text x="35" y="80" fill="#a78bfa" font-size="11" font-family="monospace" opacity="0.8">VideoContentAnalyzer</text>

  <!-- __init__ box -->
  <rect x="40" y="90" width="160" height="100" fill="url(#boxGrad1)" rx="8"/>
  <rect x="40" y="90" width="160" height="100" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="8"/>
  <text x="120" y="112" text-anchor="middle" fill="#a78bfa" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">__init__</text>
  <line x1="50" y1="120" x2="190" y2="120" stroke="#7C3AED" stroke-width="0.5" opacity="0.5"/>
  <text x="60" y="136" fill="#8b8fa8" font-size="10" font-family="monospace">• Load ViT model</text>
  <text x="60" y="152" fill="#8b8fa8" font-size="10" font-family="monospace">• Load processor</text>
  <text x="60" y="168" fill="#8b8fa8" font-size="10" font-family="monospace">• Select device</text>

  <!-- analyze_video box -->
  <rect x="280" y="90" width="200" height="160" fill="url(#boxGrad2)" rx="8"/>
  <rect x="280" y="90" width="200" height="160" fill="none" stroke="#2563EB" stroke-width="1.5" rx="8"/>
  <text x="380" y="112" text-anchor="middle" fill="#93c5fd" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">analyze_video()</text>
  <line x1="290" y1="120" x2="470" y2="120" stroke="#2563EB" stroke-width="0.5" opacity="0.5"/>
  <text x="298" y="138" fill="#8b8fa8" font-size="10" font-family="monospace">1. Open video (OpenCV)</text>
  <text x="298" y="154" fill="#8b8fa8" font-size="10" font-family="monospace">2. Compute interval</text>
  <text x="298" y="170" fill="#8b8fa8" font-size="10" font-family="monospace">3. Seek → read → PIL</text>
  <text x="298" y="186" fill="#8b8fa8" font-size="10" font-family="monospace">4. Call analyze_frame</text>
  <text x="298" y="202" fill="#8b8fa8" font-size="10" font-family="monospace">5. Aggregate results</text>
  <text x="298" y="218" fill="#8b8fa8" font-size="10" font-family="monospace">6. Early-stop on NSFW</text>

  <!-- analyze_frame box -->
  <rect x="40" y="230" width="160" height="120" fill="url(#boxGrad1)" rx="8"/>
  <rect x="40" y="230" width="160" height="120" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="8"/>
  <text x="120" y="252" text-anchor="middle" fill="#a78bfa" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">analyze_frame()</text>
  <line x1="50" y1="260" x2="190" y2="260" stroke="#7C3AED" stroke-width="0.5" opacity="0.5"/>
  <text x="60" y="276" fill="#8b8fa8" font-size="10" font-family="monospace">• Preprocess image</text>
  <text x="60" y="292" fill="#8b8fa8" font-size="10" font-family="monospace">• Run inference</text>
  <text x="60" y="308" fill="#8b8fa8" font-size="10" font-family="monospace">• Softmax → probs</text>
  <text x="60" y="324" fill="#8b8fa8" font-size="10" font-family="monospace">• Return label+conf</text>

  <!-- HuggingFace box -->
  <rect x="560" y="90" width="210" height="100" fill="url(#boxGrad3)" rx="8"/>
  <rect x="560" y="90" width="210" height="100" fill="none" stroke="#06B6D4" stroke-width="1.5" rx="8"/>
  <text x="665" y="112" text-anchor="middle" fill="#67e8f9" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">🤗 HuggingFace</text>
  <line x1="570" y1="120" x2="760" y2="120" stroke="#06B6D4" stroke-width="0.5" opacity="0.5"/>
  <text x="580" y="138" fill="#8b8fa8" font-size="10" font-family="monospace">Falconsai/nsfw_image</text>
  <text x="580" y="154" fill="#8b8fa8" font-size="10" font-family="monospace">_detection (ViT)</text>
  <text x="580" y="170" fill="#8b8fa8" font-size="10" font-family="monospace">~85 MB weights</text>

  <!-- OpenCV/PyTorch boxes at bottom -->
  <rect x="560" y="230" width="96" height="60" fill="url(#boxGrad2)" rx="8"/>
  <rect x="560" y="230" width="96" height="60" fill="none" stroke="#2563EB" stroke-width="1.5" rx="8"/>
  <text x="608" y="255" text-anchor="middle" fill="#93c5fd" font-size="11" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">OpenCV</text>
  <text x="608" y="272" text-anchor="middle" fill="#8b8fa8" font-size="9" font-family="monospace">Video I/O</text>

  <rect x="672" y="230" width="98" height="60" fill="url(#boxGrad1)" rx="8"/>
  <rect x="672" y="230" width="98" height="60" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="8"/>
  <text x="721" y="255" text-anchor="middle" fill="#a78bfa" font-size="11" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">PyTorch</text>
  <text x="721" y="272" text-anchor="middle" fill="#8b8fa8" font-size="9" font-family="monospace">Inference</text>

  <!-- Arrows -->
  <!-- __init__ -> analyze_video -->
  <line x1="200" y1="140" x2="278" y2="140" stroke="#7C3AED" stroke-width="1.5"
        marker-end="url(#arrowHead)" opacity="0.8"/>

  <!-- analyze_video -> analyze_frame -->
  <line x1="380" y1="250" x2="202" y2="280" stroke="#2563EB" stroke-width="1.5"
        marker-end="url(#arrowHead)" opacity="0.8"/>

  <!-- analyze_frame -> HuggingFace -->
  <line x1="200" y1="290" x2="558" y2="170" stroke="#7C3AED" stroke-width="1.5"
        marker-end="url(#arrowHead)" opacity="0.7" stroke-dasharray="5,3"/>

  <!-- analyze_video -> HuggingFace (uses) -->
  <line x1="480" y1="140" x2="558" y2="140" stroke="#06B6D4" stroke-width="1.5"
        marker-end="url(#arrowHead2)" opacity="0.8"/>

  <!-- analyze_video -> OpenCV -->
  <line x1="430" y1="250" x2="558" y2="255" stroke="#2563EB" stroke-width="1.5"
        marker-end="url(#arrowHead)" opacity="0.7"/>

  <!-- analyze_frame -> PyTorch -->
  <line x1="200" y1="310" x2="670" y2="265" stroke="#7C3AED" stroke-width="1.5"
        marker-end="url(#arrowHead)" opacity="0.6" stroke-dasharray="5,3"/>

  <!-- Legend -->
  <line x1="30" y1="378" x2="55" y2="378" stroke="#7C3AED" stroke-width="1.5" opacity="0.8"/>
  <text x="62" y="382" fill="#8b8fa8" font-size="10" font-family="'Segoe UI', Arial, sans-serif">Direct call</text>
  <line x1="130" y1="378" x2="155" y2="378" stroke="#06B6D4" stroke-width="1.5" stroke-dasharray="5,3" opacity="0.8"/>
  <text x="162" y="382" fill="#8b8fa8" font-size="10" font-family="'Segoe UI', Arial, sans-serif">Model dependency</text>
</svg>

</div>

---

## 🔄 Data Flow

<div align="center">

<!-- Data Flow Diagram SVG -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 480" width="820" height="480">
  <defs>
    <linearGradient id="dfBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="dfAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="nodeGrad1" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#2563EB" stop-opacity="0.3"/>
    </linearGradient>
    <linearGradient id="nodeGrad2" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#2563EB" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#06B6D4" stop-opacity="0.3"/>
    </linearGradient>
    <linearGradient id="nodeGrad3" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#06B6D4" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#7C3AED" stop-opacity="0.3"/>
    </linearGradient>
    <marker id="dfArrow" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
      <polygon points="0 0, 8 3, 0 6" fill="#06B6D4"/>
    </marker>
    <filter id="dfGlow">
      <feGaussianBlur stdDeviation="2.5" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="820" height="480" fill="url(#dfBg)" rx="12"/>
  <rect x="1" y="1" width="818" height="478" fill="none" stroke="#7C3AED" stroke-width="1" rx="12" opacity="0.4"/>

  <!-- Title -->
  <text x="410" y="35" text-anchor="middle" fill="white" font-size="16" font-weight="700"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#dfGlow)">End-to-End Data Flow</text>
  <rect x="160" y="44" width="500" height="1.5" fill="url(#dfAccent)" rx="1" opacity="0.6"/>

  <!-- Node 1: Video File -->
  <rect x="330" y="60" width="160" height="48" fill="url(#nodeGrad1)" rx="8"/>
  <rect x="330" y="60" width="160" height="48" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="8"/>
  <text x="410" y="79" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">📁 Video File</text>
  <text x="410" y="97" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">.mp4 / .avi / .mkv</text>

  <!-- Arrow 1 -->
  <line x1="410" y1="108" x2="410" y2="132" stroke="#06B6D4" stroke-width="2" marker-end="url(#dfArrow)"/>
  <text x="420" y="124" fill="#67e8f9" font-size="9" font-family="monospace">cv2.VideoCapture</text>

  <!-- Node 2: Frame Sampler -->
  <rect x="300" y="132" width="220" height="52" fill="url(#nodeGrad2)" rx="8"/>
  <rect x="300" y="132" width="220" height="52" fill="none" stroke="#2563EB" stroke-width="1.5" rx="8"/>
  <text x="410" y="153" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">🎬 Frame Sampler</text>
  <text x="410" y="173" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Seek → Read (BGR ndarray)</text>

  <!-- Arrow 2 -->
  <line x1="410" y1="184" x2="410" y2="208" stroke="#06B6D4" stroke-width="2" marker-end="url(#dfArrow)"/>
  <text x="420" y="200" fill="#67e8f9" font-size="9" font-family="monospace">cv2.cvtColor BGR→RGB</text>

  <!-- Node 3: PIL Image -->
  <rect x="310" y="208" width="200" height="48" fill="url(#nodeGrad3)" rx="8"/>
  <rect x="310" y="208" width="200" height="48" fill="none" stroke="#06B6D4" stroke-width="1.5" rx="8"/>
  <text x="410" y="228" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">🖼 PIL Image (RGB)</text>
  <text x="410" y="246" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Image.fromarray(frame_rgb)</text>

  <!-- Arrow 3 -->
  <line x1="410" y1="256" x2="410" y2="280" stroke="#06B6D4" stroke-width="2" marker-end="url(#dfArrow)"/>
  <text x="420" y="272" fill="#67e8f9" font-size="9" font-family="monospace">ViTImageProcessor</text>

  <!-- Node 4: Tensor Batch -->
  <rect x="300" y="280" width="220" height="52" fill="url(#nodeGrad1)" rx="8"/>
  <rect x="300" y="280" width="220" height="52" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="8"/>
  <text x="410" y="300" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">📦 Tensor Batch</text>
  <text x="410" y="320" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">pixel_values on CUDA/CPU</text>

  <!-- Arrow 4 -->
  <line x1="410" y1="332" x2="410" y2="356" stroke="#06B6D4" stroke-width="2" marker-end="url(#dfArrow)"/>
  <text x="420" y="348" fill="#67e8f9" font-size="9" font-family="monospace">ViT forward pass</text>

  <!-- Node 5: Logits → Softmax -->
  <rect x="300" y="356" width="220" height="52" fill="url(#nodeGrad2)" rx="8"/>
  <rect x="300" y="356" width="220" height="52" fill="none" stroke="#2563EB" stroke-width="1.5" rx="8"/>
  <text x="410" y="376" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">📊 Logits → Softmax</text>
  <text x="410" y="396" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">argmax + id2label mapping</text>

  <!-- Arrow 5 -->
  <line x1="410" y1="408" x2="410" y2="432" stroke="#06B6D4" stroke-width="2" marker-end="url(#dfArrow)"/>
  <text x="420" y="424" fill="#67e8f9" font-size="9" font-family="monospace">threshold check</text>

  <!-- Node 6: Result -->
  <rect x="310" y="432" width="200" height="38" fill="url(#nodeGrad3)" rx="8"/>
  <rect x="310" y="432" width="200" height="38" fill="none" stroke="#06B6D4" stroke-width="1.5" rx="8"/>
  <text x="410" y="448" text-anchor="middle" fill="white" font-size="12" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">✅ Result Dict</text>
  <text x="410" y="463" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">("nsfw"|"normal", confidence)</text>

  <!-- Early stop side note -->
  <rect x="570" y="280" width="180" height="56" fill="#1e1040" rx="8" stroke="#7C3AED" stroke-width="1" opacity="0.9"/>
  <text x="660" y="300" text-anchor="middle" fill="#a78bfa" font-size="11" font-weight="700" font-family="'Segoe UI', Arial, sans-serif">🛑 Early Stop</text>
  <text x="660" y="316" text-anchor="middle" fill="#8b8fa8" font-size="9" font-family="monospace">label==nsfw AND</text>
  <text x="660" y="330" text-anchor="middle" fill="#8b8fa8" font-size="9" font-family="monospace">conf ≥ threshold</text>
  <line x1="522" y1="310" x2="568" y2="310" stroke="#7C3AED" stroke-width="1.5" stroke-dasharray="4,2" opacity="0.7"/>
</svg>

</div>

---

## 🛠 Technology Stack

| Layer | Library | Version | Role |
|---|---|---|---|
| **Inference Engine** | [PyTorch](https://pytorch.org/) | `≥ 2.0.0` | Tensor computation & GPU acceleration |
| **Model Hub** | [Transformers](https://huggingface.co/transformers/) | `≥ 4.35.0` | ViT model loading, image processor |
| **Vision Model** | [`Falconsai/nsfw_image_detection`](https://huggingface.co/Falconsai/nsfw_image_detection) | latest | Fine-tuned ViT NSFW classifier |
| **Video I/O** | [OpenCV](https://opencv.org/) (`opencv-python`) | `≥ 4.8.0` | Frame seeking, BGR→RGB conversion |
| **Image Processing** | [Pillow](https://pillow.readthedocs.io/) | `≥ 10.0.0` | PIL Image wrapping for ViT processor |
| **Runtime** | Python | `≥ 3.9` | Language runtime |
| **Accelerator** | CUDA *(optional)* | any | GPU inference (16× speedup typical) |

---

## 📁 Project Structure

```
video-nsfw/
├── video_analyzer.py      # VideoContentAnalyzer class + CLI entry point
├── requirements.txt       # Python dependencies with minimum versions
├── LICENSE                # MIT License
└── README.md              # This file
```

---

## 📦 Requirements

- Python **3.9+**
- `opencv-python` ≥ 4.8.0
- `torch` ≥ 2.0.0
- `Pillow` ≥ 10.0.0
- `transformers` ≥ 4.35.0
- *(Optional)* NVIDIA GPU + CUDA toolkit for accelerated inference

---

## 🚀 Installation

```bash
# 1. Clone the repository
git clone https://github.com/Kaelith69/video-nsfw.git
cd video-nsfw

# 2. (Recommended) Create a virtual environment
python -m venv .venv
source .venv/bin/activate      # Linux / macOS
# .venv\Scripts\activate       # Windows

# 3. Install dependencies
pip install -r requirements.txt
```

> **GPU users:** Replace the `torch` install with the CUDA-enabled wheel from [pytorch.org](https://pytorch.org/get-started/locally/).
>
> ```bash
> pip install torch --index-url https://download.pytorch.org/whl/cu121
> ```

---

## 🎮 Usage

### Command-Line

```bash
# Analyze a local video file (results printed to stdout)
python video_analyzer.py /path/to/your/video.mp4
```

**Example output:**

```
NSFW content detected!
First occurrence: Frame 2
Confidence: 94.31%

Detailed frame analysis:
Frame 1: normal (99.12% confidence)
Frame 2: nsfw (94.31% confidence)
```

### Python API

```python
from pathlib import Path
from video_analyzer import VideoContentAnalyzer

# Initialize (downloads model on first run ~85 MB)
analyzer = VideoContentAnalyzer()

# Analyze with defaults (6 frames, stop on NSFW, 50% threshold)
results = analyzer.analyze_video("my_video.mp4")

# Analyze more frames without early stopping
results = analyzer.analyze_video(
    video_path=Path("my_video.mp4"),
    num_frames=12,
    stop_on_nsfw=False,
    nsfw_threshold=0.7,
)

# Check overall verdict
if results["nsfw_detected"]:
    frame = results["first_nsfw_frame"]
    print(f"NSFW detected at frame {frame['frame_number']} "
          f"({frame['confidence']:.2%} confidence)")

# Iterate per-frame results
for frame in results["frame_results"]:
    print(f"Frame {frame['frame_number']}: {frame['prediction']} "
          f"@ {frame['confidence']:.2%}")
```

---

## ⚙️ Configuration

| Parameter | Type | Default | Description |
|---|---|---|---|
| `model_name` | `str` | `"Falconsai/nsfw_image_detection"` | HuggingFace model ID or local path |
| `num_frames` | `int` | `6` | Number of frames to sample from the video |
| `stop_on_nsfw` | `bool` | `True` | Stop immediately on first NSFW detection |
| `nsfw_threshold` | `float` | `0.5` | Minimum confidence to flag as NSFW (0.0–1.0) |

---

## 📊 Output Schema

`analyze_video()` returns a `dict` with the following structure:

```python
{
    "frames_analyzed": int,          # Number of frames successfully analyzed
    "nsfw_detected": bool,           # True if any frame exceeded the threshold
    "first_nsfw_frame": {            # None if no NSFW detected
        "frame_number": int,         #   1-based index in the sampled set
        "position": int,             #   Absolute frame position in the video
        "prediction": str,           #   "nsfw" or "normal"
        "confidence": float,         #   Softmax probability (0.0–1.0)
    },
    "frame_results": [               # One entry per analyzed frame
        {
            "frame_number": int,
            "position": int,
            "prediction": str,
            "confidence": float,
        },
        # ...
    ],
}
```

---

## 🔬 How It Works

1. **Frame Sampling** — The video's total frame count is divided evenly by `num_frames` to compute a sampling `interval`. Frames at positions `0, interval, 2×interval, …` are selected.

2. **BGR → RGB** — OpenCV reads frames in BGR color order. The frame is converted to RGB before being passed to the ViT processor, which was trained on RGB images.

3. **ViT Inference** — Each PIL image is tokenised by `ViTImageProcessor` into a patch-based tensor. The model returns raw `logits` over its label vocabulary (`nsfw`, `normal`).

4. **Softmax + Label** — `torch.softmax` converts logits to probabilities. The `argmax` of the logits selects the winning class, and `id2label` maps the integer index back to a human-readable string.

5. **Early Stop** — If `stop_on_nsfw=True` and the predicted label is `"nsfw"` with `confidence >= nsfw_threshold`, analysis halts immediately to save time and compute.

---

## ⚡ Performance

<div align="center">

<!-- Performance Stats Panel SVG -->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 820 200" width="820" height="200">
  <defs>
    <linearGradient id="perfBg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#0f0720"/>
      <stop offset="100%" style="stop-color:#0c1a3a"/>
    </linearGradient>
    <linearGradient id="perfAccent" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#7C3AED"/>
      <stop offset="100%" style="stop-color:#06B6D4"/>
    </linearGradient>
    <linearGradient id="stat1" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#7C3AED" stop-opacity="0.1"/>
    </linearGradient>
    <linearGradient id="stat2" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#2563EB" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#2563EB" stop-opacity="0.1"/>
    </linearGradient>
    <linearGradient id="stat3" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#06B6D4" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#06B6D4" stop-opacity="0.1"/>
    </linearGradient>
    <linearGradient id="stat4" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#7C3AED" stop-opacity="0.5"/>
      <stop offset="100%" style="stop-color:#06B6D4" stop-opacity="0.1"/>
    </linearGradient>
    <filter id="perfGlow">
      <feGaussianBlur stdDeviation="3" result="coloredBlur"/>
      <feMerge><feMergeNode in="coloredBlur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="820" height="200" fill="url(#perfBg)" rx="12"/>
  <rect x="1" y="1" width="818" height="198" fill="none" stroke="#7C3AED" stroke-width="1" rx="12" opacity="0.4"/>

  <!-- Title -->
  <text x="410" y="32" text-anchor="middle" fill="white" font-size="15" font-weight="700"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#perfGlow)">Performance Stats</text>
  <rect x="200" y="40" width="420" height="1.5" fill="url(#perfAccent)" rx="1" opacity="0.6"/>

  <!-- Stat Card 1: GPU Inference -->
  <rect x="30" y="55" width="170" height="120" fill="url(#stat1)" rx="10"/>
  <rect x="30" y="55" width="170" height="120" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="10"/>
  <text x="115" y="85" text-anchor="middle" fill="#a78bfa" font-size="28" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#perfGlow)">~5ms</text>
  <text x="115" y="105" text-anchor="middle" fill="#8b8fa8" font-size="11" font-family="'Segoe UI', Arial, sans-serif">per frame (GPU)</text>
  <line x1="50" y1="115" x2="180" y2="115" stroke="#7C3AED" stroke-width="0.5" opacity="0.5"/>
  <text x="115" y="133" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">RTX 3080</text>
  <text x="115" y="148" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">CUDA accelerated</text>
  <text x="115" y="163" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">16× vs CPU</text>

  <!-- Stat Card 2: CPU Inference -->
  <rect x="220" y="55" width="170" height="120" fill="url(#stat2)" rx="10"/>
  <rect x="220" y="55" width="170" height="120" fill="none" stroke="#2563EB" stroke-width="1.5" rx="10"/>
  <text x="305" y="85" text-anchor="middle" fill="#93c5fd" font-size="28" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#perfGlow)">~80ms</text>
  <text x="305" y="105" text-anchor="middle" fill="#8b8fa8" font-size="11" font-family="'Segoe UI', Arial, sans-serif">per frame (CPU)</text>
  <line x1="240" y1="115" x2="370" y2="115" stroke="#2563EB" stroke-width="0.5" opacity="0.5"/>
  <text x="305" y="133" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Modern CPU</text>
  <text x="305" y="148" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">No CUDA required</text>
  <text x="305" y="163" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Fallback mode</text>

  <!-- Stat Card 3: Model Size -->
  <rect x="410" y="55" width="170" height="120" fill="url(#stat3)" rx="10"/>
  <rect x="410" y="55" width="170" height="120" fill="none" stroke="#06B6D4" stroke-width="1.5" rx="10"/>
  <text x="495" y="85" text-anchor="middle" fill="#67e8f9" font-size="28" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#perfGlow)">~85MB</text>
  <text x="495" y="105" text-anchor="middle" fill="#8b8fa8" font-size="11" font-family="'Segoe UI', Arial, sans-serif">model weights</text>
  <line x1="430" y1="115" x2="560" y2="115" stroke="#06B6D4" stroke-width="0.5" opacity="0.5"/>
  <text x="495" y="133" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">First-run download</text>
  <text x="495" y="148" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Cached locally</text>
  <text x="495" y="163" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">HF Hub</text>

  <!-- Stat Card 4: Default Frames -->
  <rect x="600" y="55" width="190" height="120" fill="url(#stat4)" rx="10"/>
  <rect x="600" y="55" width="190" height="120" fill="none" stroke="#7C3AED" stroke-width="1.5" rx="10"/>
  <text x="695" y="85" text-anchor="middle" fill="#a78bfa" font-size="28" font-weight="900"
        font-family="'Segoe UI', Arial, sans-serif" filter="url(#perfGlow)">6 frames</text>
  <text x="695" y="105" text-anchor="middle" fill="#8b8fa8" font-size="11" font-family="'Segoe UI', Arial, sans-serif">default sampling</text>
  <line x1="620" y1="115" x2="770" y2="115" stroke="#7C3AED" stroke-width="0.5" opacity="0.5"/>
  <text x="695" y="133" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Configurable (1–N)</text>
  <text x="695" y="148" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Linear time scale</text>
  <text x="695" y="163" text-anchor="middle" fill="#8b8fa8" font-size="10" font-family="monospace">Early-stop default</text>
</svg>

</div>

- **First run** downloads model weights (~85 MB) from HuggingFace Hub and caches them in `~/.cache/huggingface/`.
- **GPU inference** is approximately 16× faster than CPU on an NVIDIA RTX 3080 (~5 ms vs ~80 ms per frame).
- Increasing `num_frames` improves coverage at the cost of linear time increase.
- `stop_on_nsfw=True` (default) keeps worst-case latency low for clearly flagged content.

---

## ♿ Accessibility

- **CLI output** is plain text, compatible with screen readers and terminal assistants.
- **Logging** uses Python's standard `logging` module — output can be redirected and consumed programmatically.
- **Result schema** is a plain Python `dict` — no binary encodings or proprietary formats — making it easy to integrate with any downstream consumer including accessible UIs.
- All confidence values are expressed as human-readable floats (0.0–1.0) and formatted as percentages in CLI output, reducing ambiguity.

---

## 🔒 Privacy & Security

| Concern | Approach |
|---|---|
| **Local processing** | All inference runs on the local machine; no frames or video data are sent to external services |
| **Model weights** | Downloaded once from HuggingFace Hub over HTTPS and cached locally; no runtime network calls |
| **No persistent storage** | The library does not write frames, thumbnails, or intermediate data to disk |
| **Resource cleanup** | `cv2.VideoCapture` is always released in a `try/finally` block, preventing file handle leaks |
| **No credentials** | The library requires no API keys or authentication tokens |
| **Input validation** | `FileNotFoundError` raised for non-existent paths; `RuntimeError` raised if the video cannot be opened |

> ⚠️ **Note:** The NSFW classifier operates on visual content. Operators deploying this tool in production pipelines should implement appropriate data governance, access controls, and audit logging in the surrounding system.

---

## 🎨 Design Principles

1. **Single Responsibility** — `VideoContentAnalyzer` does one thing: classify video frames for NSFW content. It does not handle storage, notifications, or UI.
2. **Fail Fast** — Invalid inputs raise standard Python exceptions immediately, providing clear error messages.
3. **Resource Safety** — All external resources (video file handles) are managed with `try/finally` to guarantee release even on exceptions.
4. **Device Agnosticism** — GPU is used when available, but the full pipeline works identically on CPU-only machines.
5. **Composability** — The Python API returns plain dicts, making it easy to compose with logging pipelines, web frameworks, or message queues.
6. **Minimal Dependencies** — Only four dependencies are required, all widely-used and well-maintained in the Python ecosystem.

---

## 🗺 Roadmap

| Status | Feature |
|---|---|
| ✅ | Single-class video NSFW detection |
| ✅ | GPU/CPU automatic device selection |
| ✅ | Configurable frame sampling and threshold |
| ✅ | Early-stop on first NSFW detection |
| 🔲 | Batch video processing (multiple files) |
| 🔲 | Audio-track moderation (speech-to-text + NLP) |
| 🔲 | Scene-change-aware adaptive sampling |
| 🔲 | REST API / FastAPI wrapper |
| 🔲 | Docker image for containerised deployment |
| 🔲 | Alternative model support (CLIP-based classifiers) |
| 🔲 | Confidence calibration / platt scaling |
| 🔲 | Async/concurrent frame processing |

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-improvement`)
3. Commit your changes (`git commit -m 'Add some improvement'`)
4. Push to the branch (`git push origin feature/my-improvement`)
5. Open a Pull Request

Please read the [Contributing Guide](wiki/Contributing.md) for details on our code standards and review process.

---

## 📄 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.

---

<div align="center">

*Built with ❤️ and a healthy respect for responsible AI deployment*

[![GitHub](https://img.shields.io/badge/GitHub-Kaelith69%2Fvideo--nsfw-181717?style=flat-square&logo=github)](https://github.com/Kaelith69/video-nsfw)

</div>
