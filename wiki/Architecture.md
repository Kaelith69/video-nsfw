# Architecture

This page provides a deep technical walkthrough of the `video-nsfw` system architecture, component design, and internal data flow.

---

## System Overview

`video-nsfw` is a single-module Python library consisting of one class, `VideoContentAnalyzer`, with two public methods. The design is deliberately minimal: maximum functionality with minimum surface area.

```
┌─────────────────────────────────────────────────────────────────────┐
│                        video_analyzer.py                            │
│                                                                     │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │                   VideoContentAnalyzer                        │  │
│  │                                                               │  │
│  │  __init__(model_name)          analyze_video(path, ...)       │  │
│  │  ├── Load ViT model            ├── Validate path              │  │
│  │  ├── Load ViTImageProcessor    ├── Open VideoCapture          │  │
│  │  ├── Select device (GPU/CPU)   ├── Compute frame interval     │  │
│  │  └── Configure logging         ├── Loop: seek → read → PIL   │  │
│  │                                ├── Call analyze_frame()       │  │
│  │  analyze_frame(pil_image)      ├── Aggregate results dict     │  │
│  │  ├── Preprocess (processor)    ├── Early-stop on NSFW         │  │
│  │  ├── Forward pass (model)      └── Release VideoCapture       │  │
│  │  ├── Softmax probabilities                                     │  │
│  │  └── argmax + id2label                                        │  │
│  └───────────────────────────────────────────────────────────────┘  │
│                                                                     │
│  External Dependencies:                                             │
│  ├── opencv-python  (cv2)        — Video I/O, color conversion     │
│  ├── Pillow         (PIL)        — Image wrapping                   │
│  ├── torch                       — Tensor ops, device management    │
│  └── transformers                — Model loading, ViTImageProcessor │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Component Design

### `__init__` — Initialisation

**Purpose:** Load and configure all AI model components once at startup.

```python
def __init__(self, model_name: str = "Falconsai/nsfw_image_detection"):
```

**Steps:**
1. **Device selection** — Checks `torch.cuda.is_available()`. Uses `cuda` if present, else `cpu`. This is set once and used for all subsequent tensor operations.
2. **Model loading** — `AutoModelForImageClassification.from_pretrained(model_name)` downloads (first run) or loads from cache the ViT model weights and moves them to the selected device.
3. **Processor loading** — `ViTImageProcessor.from_pretrained(model_name)` loads the image preprocessing configuration (resize, normalise, patch extraction).
4. **Logger setup** — Standard Python `logging` configured at `INFO` level.

**Design note:** Loading happens once in `__init__`, not per-call. This is critical for performance in batch or repeated use — model loading is expensive (~85 MB + inference graph compilation).

---

### `analyze_frame` — Single Frame Classification

**Purpose:** Classify one PIL image as `nsfw` or `normal` with a confidence score.

```python
def analyze_frame(self, image: Image.Image) -> Tuple[str, float]:
```

**Steps:**
1. **Preprocessing** — `ViTImageProcessor` resizes the image to 224×224, normalises pixel values, and converts to a PyTorch tensor batch (`{"pixel_values": Tensor}`).
2. **Device transfer** — Inputs are moved to the same device as the model (`.to(self.device)`).
3. **Inference** — `torch.no_grad()` context manager disables gradient tracking (saves memory; not needed for inference). The model forward pass produces `logits`.
4. **Softmax** — `torch.softmax(logits, dim=-1)` converts raw logits to probabilities that sum to 1.
5. **Label resolution** — `logits.argmax(-1).item()` finds the highest-scoring class index. `self.model.config.id2label[pred_idx]` maps the integer index to a string label.

**Returns:** `Tuple[str, float]` — e.g., `("nsfw", 0.9431)` or `("normal", 0.9912)`.

---

### `analyze_video` — Full Video Analysis

**Purpose:** Orchestrate frame extraction from a video file and run `analyze_frame` on sampled frames.

```python
def analyze_video(
    self,
    video_path: Union[str, Path],
    num_frames: int = 6,
    stop_on_nsfw: bool = True,
    nsfw_threshold: float = 0.5,
) -> dict:
```

**Steps:**

1. **Path validation** — Converts input to `pathlib.Path` and checks existence.
2. **Video open** — `cv2.VideoCapture(str(video_path))` opens the video. Raises `RuntimeError` if the file cannot be decoded.
3. **Interval calculation** — `interval = max(1, total_frames // num_frames)`. Ensures at least 1, even for very short videos.
4. **Frame loop** — For each `i` in `range(num_frames)`:
   - `frame_position = min(i * interval, total_frames - 1)` — clamped to avoid seeking past the end.
   - `cap.set(cv2.CAP_PROP_POS_FRAMES, frame_position)` — seeks to the target frame.
   - `cap.read()` — decodes the frame as a BGR `ndarray`.
   - `cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)` — converts to RGB.
   - `Image.fromarray(frame_rgb)` — wraps as PIL Image.
   - `self.analyze_frame(pil_image)` — classifies the frame.
5. **Result aggregation** — Each frame result is appended to `frame_results`. If NSFW is detected above threshold, `nsfw_detected` and `first_nsfw_frame` are set.
6. **Early stop** — If `stop_on_nsfw=True` and a frame is flagged, the loop breaks.
7. **Resource cleanup** — `cap.release()` in the `finally` block guarantees the file handle is released.

**Returns:** A result dict (see Output Schema in README).

---

## Model: Falconsai/nsfw_image_detection

The model used is a **Vision Transformer (ViT)** fine-tuned for binary NSFW classification:

| Property | Value |
|---|---|
| Architecture | ViT (Vision Transformer) |
| Base model | `google/vit-base-patch16-224` |
| Fine-tuned by | [Falconsai](https://huggingface.co/Falconsai) |
| Labels | `nsfw`, `normal` |
| Input size | 224 × 224 pixels |
| Weights size | ~85 MB |
| HuggingFace Hub | `Falconsai/nsfw_image_detection` |

### How ViT Works

1. The input image (224×224) is divided into a grid of 16×16 pixel patches.
2. Each patch is linearly projected to a vector embedding.
3. A `[CLS]` token is prepended; positional embeddings are added.
4. The sequence passes through multiple Transformer encoder layers.
5. The `[CLS]` output is fed to a classification head (linear layer) that produces logits for each class.

---

## Device Management

```
torch.cuda.is_available()
        │
   ┌────┴─────┐
  True       False
   │           │
CUDA GPU     CPU
(fast)      (fallback)
```

The device is selected once in `__init__` and stored as `self.device`. Both the model and all input tensors are moved to this device, ensuring consistent computation.

---

## Error Handling

| Condition | Exception |
|---|---|
| Video file does not exist | `FileNotFoundError` |
| Video file cannot be opened/decoded | `RuntimeError("Failed to open video file")` |
| Frame read failure | Logged as warning; frame skipped |
| Any other exception | Propagates to caller; `VideoCapture` still released |

---

## Logging

The library uses Python's standard `logging` module:

| Level | Message |
|---|---|
| `INFO` | Analysis start, per-frame classification results |
| `WARNING` | Failed frame reads, NSFW detection with early stop |

Log output can be suppressed by configuring the root logger or the `video_analyzer` logger:

```python
import logging
logging.getLogger("video_analyzer").setLevel(logging.ERROR)
```

---

## Sequence Diagram

```
Caller          VideoContentAnalyzer      cv2          ViT Model
  │                     │                  │               │
  │  __init__()         │                  │               │
  │────────────────────▶│                  │               │
  │                     │  from_pretrained ├───────────────▶
  │                     │◀────────────────────────────────│
  │                     │                  │               │
  │  analyze_video(path)│                  │               │
  │────────────────────▶│                  │               │
  │                     │  VideoCapture(path)              │
  │                     │─────────────────▶│               │
  │                     │  [loop N frames] │               │
  │                     │  cap.read()      │               │
  │                     │◀─────────────────│               │
  │                     │  analyze_frame() │               │
  │                     │  processor(img)  │               │
  │                     │  model(**inputs) │               │
  │                     │────────────────────────────────▶│
  │                     │◀────────────────────────────────│
  │                     │  [early stop?]   │               │
  │                     │  cap.release()   │               │
  │                     │─────────────────▶│               │
  │◀────────────────────│                  │               │
  │  result dict        │                  │               │
```
