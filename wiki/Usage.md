# Usage

Complete reference for the `video-nsfw` command-line interface and Python API.

---

## Command-Line Interface (CLI)

### Synopsis

```
python video_analyzer.py [VIDEO_PATH]
```

### Arguments

| Argument | Description | Default |
|---|---|---|
| `VIDEO_PATH` | Path to the video file to analyze | `video.mp4` (current directory) |

> **Note:** All advanced options (`num_frames`, `nsfw_threshold`, etc.) are only available via the Python API. The CLI uses default values.

### CLI Defaults

| Parameter | Value |
|---|---|
| `num_frames` | 6 |
| `stop_on_nsfw` | `True` |
| `nsfw_threshold` | 0.5 |

### Examples

```bash
# Analyze a specific file
python video_analyzer.py /home/user/videos/clip.mp4

# Analyze a file in the current directory
python video_analyzer.py my_video.avi

# Use the default filename (video.mp4 in current directory)
python video_analyzer.py
```

### CLI Output Format

**When NSFW content is detected:**

```
NSFW content detected!
First occurrence: Frame 3
Confidence: 87.42%

Detailed frame analysis:
Frame 1: normal (98.15% confidence)
Frame 2: normal (95.30% confidence)
Frame 3: nsfw (87.42% confidence)
```

**When no NSFW content is detected:**

```
No NSFW content detected in 6 analyzed frames

Detailed frame analysis:
Frame 1: normal (99.12% confidence)
Frame 2: normal (97.80% confidence)
Frame 3: normal (98.45% confidence)
Frame 4: normal (99.01% confidence)
Frame 5: normal (96.73% confidence)
Frame 6: normal (98.22% confidence)
```

**Exit codes:**

| Code | Meaning |
|---|---|
| `0` | Analysis completed successfully |
| `1` | Error (file not found, video decode failure, etc.) |

---

## Python API

### Importing

```python
from video_analyzer import VideoContentAnalyzer
```

### Class: `VideoContentAnalyzer`

#### Constructor

```python
VideoContentAnalyzer(model_name: str = "Falconsai/nsfw_image_detection")
```

**Parameters:**

| Parameter | Type | Default | Description |
|---|---|---|---|
| `model_name` | `str` | `"Falconsai/nsfw_image_detection"` | HuggingFace model ID or path to a local model directory |

**Side effects:**
- Downloads model weights on first call (~85 MB).
- Moves model to CUDA GPU if available, otherwise CPU.
- Configures Python logging at `INFO` level.

**Example:**

```python
# Default model
analyzer = VideoContentAnalyzer()

# Custom model
analyzer = VideoContentAnalyzer(model_name="my-org/my-nsfw-model")

# Local model directory
analyzer = VideoContentAnalyzer(model_name="/models/nsfw_vit")
```

---

#### Method: `analyze_video`

```python
analyze_video(
    video_path: Union[str, Path],
    num_frames: int = 6,
    stop_on_nsfw: bool = True,
    nsfw_threshold: float = 0.5,
) -> dict
```

**Parameters:**

| Parameter | Type | Default | Description |
|---|---|---|---|
| `video_path` | `str` or `Path` | *(required)* | Path to the video file |
| `num_frames` | `int` | `6` | Number of frames to sample (evenly spaced) |
| `stop_on_nsfw` | `bool` | `True` | Halt analysis immediately on first NSFW detection |
| `nsfw_threshold` | `float` | `0.5` | Confidence score threshold for NSFW classification (0.0–1.0) |

**Returns:** `dict` — See [Output Schema](#output-schema) below.

**Raises:**

| Exception | Condition |
|---|---|
| `FileNotFoundError` | `video_path` does not exist |
| `RuntimeError` | Video file cannot be opened or decoded |

---

#### Method: `analyze_frame`

```python
analyze_frame(image: Image.Image) -> Tuple[str, float]
```

**Parameters:**

| Parameter | Type | Description |
|---|---|---|
| `image` | `PIL.Image.Image` | RGB image to classify |

**Returns:** `Tuple[str, float]` — `(label, confidence)` where `label` is `"nsfw"` or `"normal"` and `confidence` is the softmax probability (0.0–1.0).

**Note:** This method can be used independently to classify individual images, not just video frames:

```python
from PIL import Image
img = Image.open("screenshot.png")
label, confidence = analyzer.analyze_frame(img)
print(f"{label} ({confidence:.2%})")
```

---

## Output Schema

`analyze_video()` returns:

```python
{
    "frames_analyzed": int,      # Count of successfully decoded frames
    "nsfw_detected": bool,       # True if any frame exceeded nsfw_threshold
    "first_nsfw_frame": {        # None if nsfw_detected is False
        "frame_number": int,     # 1-based index within sampled frames
        "position": int,         # Absolute frame index in the video
        "prediction": str,       # "nsfw" or "normal"
        "confidence": float,     # Softmax probability (0.0–1.0)
    },
    "frame_results": [
        {
            "frame_number": int,
            "position": int,
            "prediction": str,
            "confidence": float,
        },
        # One entry per analyzed frame
    ],
}
```

---

## Usage Patterns

### Pattern 1: Quick Scan (Default)

Fastest way to check a video with early stop:

```python
from video_analyzer import VideoContentAnalyzer

analyzer = VideoContentAnalyzer()
results = analyzer.analyze_video("video.mp4")

if results["nsfw_detected"]:
    print("NSFW detected")
else:
    print("Clean")
```

### Pattern 2: Thorough Scan (No Early Stop)

Scan all frames to get a complete picture:

```python
results = analyzer.analyze_video(
    "video.mp4",
    num_frames=20,
    stop_on_nsfw=False,
    nsfw_threshold=0.6,
)

nsfw_frames = [f for f in results["frame_results"] if f["prediction"] == "nsfw"]
print(f"NSFW frames: {len(nsfw_frames)} / {results['frames_analyzed']}")
```

### Pattern 3: High-Precision Mode

Raise the threshold to reduce false positives:

```python
results = analyzer.analyze_video(
    "video.mp4",
    num_frames=12,
    nsfw_threshold=0.85,
)
```

### Pattern 4: Batch Processing

Process multiple videos in a loop:

```python
from pathlib import Path
from video_analyzer import VideoContentAnalyzer

analyzer = VideoContentAnalyzer()  # Initialize once

video_dir = Path("/media/uploads")
for video_path in video_dir.glob("*.mp4"):
    results = analyzer.analyze_video(video_path, num_frames=8)
    status = "NSFW" if results["nsfw_detected"] else "CLEAN"
    print(f"{video_path.name}: {status}")
```

### Pattern 5: Image Classification

Use `analyze_frame` directly on images:

```python
from PIL import Image
from video_analyzer import VideoContentAnalyzer

analyzer = VideoContentAnalyzer()

for img_path in Path("images/").glob("*.jpg"):
    img = Image.open(img_path).convert("RGB")
    label, confidence = analyzer.analyze_frame(img)
    print(f"{img_path.name}: {label} ({confidence:.2%})")
```

### Pattern 6: Integration with Logging

Suppress library logs in production:

```python
import logging
logging.getLogger("video_analyzer").setLevel(logging.ERROR)

from video_analyzer import VideoContentAnalyzer
analyzer = VideoContentAnalyzer()
results = analyzer.analyze_video("video.mp4")
```

---

## Supported Video Formats

Any format supported by the installed OpenCV build. Common formats include:

| Format | Extension |
|---|---|
| MP4 (H.264/H.265) | `.mp4` |
| AVI | `.avi` |
| MKV | `.mkv` |
| MOV (QuickTime) | `.mov` |
| WebM | `.webm` |
| FLV | `.flv` |

> Format support depends on the codecs available in your OpenCV installation. `opencv-python` (the pip package) includes the most common codecs.
