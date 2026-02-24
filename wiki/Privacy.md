# Privacy & Security

This page documents the data handling practices, security model, and compliance considerations for `video-nsfw`.

---

## Data Processing Model

`video-nsfw` is designed with **local-only processing** as a core principle. No video data, frames, or analysis results are transmitted to any external service.

### What Happens to Your Data

| Stage | Data | Destination | Retained? |
|---|---|---|---|
| Video file open | File handle | Local memory | No — released in `finally` block |
| Frame decode | BGR ndarray | Local memory (RAM) | No — overwritten each iteration |
| Color conversion | RGB ndarray | Local memory | No — immediately wrapped as PIL |
| PIL Image | Image object | Local memory | No — discarded after inference |
| Tensor batch | `pixel_values` tensor | GPU/CPU VRAM or RAM | No — released when `torch.no_grad()` exits |
| Model output | logits, probabilities | Local memory | No — only `label` and `confidence` scalars kept |
| Results dict | Classification strings and floats | Caller's memory | At caller's discretion |

**No frames, thumbnails, or intermediate representations are written to disk by the library.**

---

## Network Activity

| Activity | When | What is Transmitted |
|---|---|---|
| Model download | First run only | HTTP GET to `huggingface.co` for model weights (~85 MB) |
| Subsequent runs | Never | Nothing — model is loaded from local cache |

After the model is cached locally (`~/.cache/huggingface/`), the library operates fully offline.

To verify no network calls occur after caching:

```python
import os
os.environ["TRANSFORMERS_OFFLINE"] = "1"  # Force offline mode

from video_analyzer import VideoContentAnalyzer
analyzer = VideoContentAnalyzer()  # Will raise if model not cached
```

---

## Security Considerations

### Input Validation

| Input | Validation |
|---|---|
| `video_path` | Checked for existence via `Path.exists()` before any I/O |
| `nsfw_threshold` | Not range-checked; values outside [0.0, 1.0] are caller responsibility |
| `num_frames` | Not range-checked; `max(1, ...)` guards against division-by-zero |
| `model_name` | Passed directly to HuggingFace `from_pretrained`; only trusted model IDs should be used |

### Resource Safety

The `cv2.VideoCapture` handle is always released, even if an exception is raised during frame processing:

```python
try:
    # ... frame processing loop
finally:
    cap.release()  # Always executed
```

This prevents file descriptor leaks in long-running services.

### Model Trust

The library loads a pre-trained model from HuggingFace Hub. When using the default model (`Falconsai/nsfw_image_detection`):

- Weights are downloaded over HTTPS.
- The model is a standard PyTorch checkpoint; it does not execute arbitrary code.
- HuggingFace model card: [https://huggingface.co/Falconsai/nsfw_image_detection](https://huggingface.co/Falconsai/nsfw_image_detection)

> ⚠️ If you use a custom `model_name`, ensure you trust the model source. Loading untrusted model checkpoints (especially `pickle`-based formats) can execute arbitrary code.

### No Credential Requirements

The library does not require API keys, authentication tokens, or any form of credentials. The HuggingFace model download uses public endpoints.

---

## Deployment Considerations

When integrating `video-nsfw` into a production system, operators should consider the following at the **system level** (outside the scope of this library):

### Access Control

- Restrict access to video files being analyzed to authorised processes only.
- Run the analysis process with minimum required file system permissions.

### Audit Logging

- Log analysis events (file path, timestamp, verdict, confidence) in your surrounding system for audit trails.
- Do **not** log frame content or video data.

### Data Retention

- The library returns classification metadata (labels, confidence scores) only — not image data.
- Define a data retention policy for the result dicts in your system.

### Sensitive Content Handling

- Analysts and systems that process the NSFW detection results should follow your organisation's content moderation policies.
- Results should only be accessible to authorised personnel.

### Container/Sandbox Isolation

For maximum isolation when processing untrusted video files, consider running the analyzer in a container or sandbox with:

- No outbound network access (after model is cached)
- Read-only access to the video source directory
- No write access to sensitive paths

---

## Privacy Regulations

`video-nsfw` itself does not collect, store, or process personal data. However, operators deploying it to analyse user-submitted content should ensure compliance with applicable regulations (e.g., GDPR, CCPA) regarding:

- The video content being analyzed (which may contain personal data)
- Any results stored about individual users or content items
- Consent and transparency obligations for content moderation

This library is a technical tool; legal compliance responsibility rests with the deploying organisation.

---

## Reporting Security Issues

If you discover a security vulnerability in `video-nsfw`, please report it by opening a GitHub issue at [https://github.com/Kaelith69/video-nsfw/issues](https://github.com/Kaelith69/video-nsfw/issues) with the label `security`. For sensitive disclosures, contact the repository owner directly via GitHub.
