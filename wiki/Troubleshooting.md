# Troubleshooting

This page covers common issues, error messages, debugging techniques, and frequently asked questions.

---

## Quick Diagnostics

Run this script to check your environment before anything else:

```python
import sys
print("Python:", sys.version)

try:
    import cv2
    print("OpenCV:", cv2.__version__)
except ImportError as e:
    print("OpenCV MISSING:", e)

try:
    import torch
    print("PyTorch:", torch.__version__)
    print("CUDA available:", torch.cuda.is_available())
    if torch.cuda.is_available():
        print("GPU:", torch.cuda.get_device_name(0))
except ImportError as e:
    print("PyTorch MISSING:", e)

try:
    from PIL import Image
    import PIL
    print("Pillow:", PIL.__version__)
except ImportError as e:
    print("Pillow MISSING:", e)

try:
    import transformers
    print("Transformers:", transformers.__version__)
except ImportError as e:
    print("Transformers MISSING:", e)
```

---

## Common Errors

### `ModuleNotFoundError: No module named 'cv2'`

**Cause:** `opencv-python` is not installed.

**Fix:**
```bash
pip install opencv-python>=4.8.0
```

---

### `ModuleNotFoundError: No module named 'torch'`

**Cause:** PyTorch is not installed.

**Fix (CPU):**
```bash
pip install torch>=2.0.0
```

**Fix (GPU/CUDA 12.1):**
```bash
pip install torch --index-url https://download.pytorch.org/whl/cu121
```

---

### `FileNotFoundError: Video file not found: my_video.mp4`

**Cause:** The path provided does not point to an existing file.

**Fix:** Check the path is correct and the file exists:
```bash
ls -la my_video.mp4          # Linux/macOS
dir my_video.mp4             # Windows
```

Use an absolute path to avoid working-directory ambiguity:
```python
from pathlib import Path
analyzer.analyze_video(Path("/absolute/path/to/video.mp4"))
```

---

### `RuntimeError: Failed to open video file`

**Cause:** The file exists but OpenCV cannot decode it. This usually means:
- The file is corrupt or incomplete.
- The video codec is not supported by your OpenCV build.
- The file is a valid container but the codec library is missing.

**Fix:**
```bash
# Check if FFmpeg can decode the file
ffmpeg -i my_video.mp4

# Re-encode to H.264 MP4 (widely supported)
ffmpeg -i my_video.mkv -c:v libx264 -c:a aac output.mp4
```

---

### `OSError: [Errno 28] No space left on device`

**Cause:** The HuggingFace model cache directory is full (model is ~85 MB).

**Fix:**
```bash
# Free space or change the cache directory
export HF_HOME=/path/to/larger/disk
python video_analyzer.py my_video.mp4
```

---

### `ConnectionError` / `requests.exceptions.ConnectionError` during model download

**Cause:** No internet connection on first run, or HuggingFace Hub is temporarily unavailable.

**Fix:**
- Ensure internet connectivity and retry.
- If in an air-gapped environment, pre-download the model on a connected machine:
  ```python
  from transformers import AutoModelForImageClassification, ViTImageProcessor
  AutoModelForImageClassification.from_pretrained("Falconsai/nsfw_image_detection")
  ViTImageProcessor.from_pretrained("Falconsai/nsfw_image_detection")
  ```
  Then copy `~/.cache/huggingface/` to the target machine.

---

### `CUDA out of memory`

**Cause:** The GPU does not have enough VRAM for the model and input tensor.

**Fix (Option 1):** Force CPU mode:
```python
import torch
# Monkey-patch before importing the analyzer
torch.cuda.is_available = lambda: False

from video_analyzer import VideoContentAnalyzer
analyzer = VideoContentAnalyzer()
```

**Fix (Option 2):** Clear the GPU cache between calls:
```python
import torch
import gc

results = analyzer.analyze_video("video.mp4")
torch.cuda.empty_cache()
gc.collect()
```

---

### `Warning: Failed to read frame at position X`

**Cause:** The video is shorter than expected (frame count mismatch), the video is corrupt, or the frame seek failed.

**Behaviour:** The frame is skipped; analysis continues with remaining frames. `frames_analyzed` in the result will be less than `num_frames`.

**This is not a fatal error.** If it happens frequently, consider reducing `num_frames` to ensure they fall within the video length.

---

### Analysis returns `frames_analyzed: 0`

**Cause:** Every frame read failed. This typically indicates a corrupt video file.

**Fix:**
```bash
# Verify the video is intact
ffprobe -v error -show_entries stream=codec_name,width,height my_video.mp4
```

---

### All frames classified as `normal` (suspected false negatives)

**Possible causes:**
- The NSFW content is concentrated in frames not sampled (increase `num_frames`).
- Confidence scores are below the threshold (lower `nsfw_threshold`).
- The content type is not well-represented in the model's training data.

**Debugging:**
```python
results = analyzer.analyze_video(
    "video.mp4",
    num_frames=20,
    stop_on_nsfw=False,
    nsfw_threshold=0.3,  # Lower threshold to see borderline predictions
)
for frame in results["frame_results"]:
    print(f"Frame {frame['frame_number']}: {frame['prediction']} "
          f"({frame['confidence']:.4f})")
```

---

## Performance Issues

### Analysis is very slow

**Symptom:** Each frame takes >1 second to classify.

**Likely cause:** Running on CPU without GPU acceleration.

**Check:**
```python
import torch
print("CUDA available:", torch.cuda.is_available())
```

**Fix:** Install CUDA-enabled PyTorch (see [Installation](Installation)).

### High memory usage

**Cause:** The ViT model (~85 MB weights) and intermediate tensors are held in memory for the lifetime of the `VideoContentAnalyzer` instance.

**Mitigation:** For one-shot use in scripts, create the analyzer, run analysis, then delete the instance:
```python
analyzer = VideoContentAnalyzer()
results = analyzer.analyze_video("video.mp4")
del analyzer
import gc; gc.collect()
```

---

## Frequently Asked Questions

### Q: Can I use a different NSFW detection model?

**A:** Yes. Pass any HuggingFace image classification model compatible with `AutoModelForImageClassification` and `ViTImageProcessor`:

```python
analyzer = VideoContentAnalyzer(model_name="your-org/your-model")
```

The model must have labels named `"nsfw"` (case-insensitive check) for the threshold logic to work correctly.

---

### Q: Can I analyze images instead of videos?

**A:** Yes, use `analyze_frame` directly:

```python
from PIL import Image
img = Image.open("image.jpg").convert("RGB")
label, confidence = analyzer.analyze_frame(img)
```

---

### Q: Is there a REST API or web interface?

**A:** Not in the current version. See the [Roadmap](Roadmap) for planned API wrapper support.

---

### Q: Does it work on macOS Apple Silicon (M1/M2/M3)?

**A:** Yes, on CPU. PyTorch Metal (MPS) acceleration is not currently enabled by the automatic device selection. You can manually add MPS support by modifying the `__init__` method to check `torch.backends.mps.is_available()`.

---

### Q: How many frames should I sample?

**A:** The default of 6 is a good balance for general use. For longer videos (>10 minutes) or videos where NSFW content may appear briefly, increase to 12–24. For very short clips (<30 seconds), 3–6 frames is typically sufficient.

---

### Q: What does `nsfw_threshold=0.5` mean?

**A:** If the model's softmax probability for the `nsfw` class is ≥ 0.5 (50%), the frame is classified as NSFW. Increasing this value (e.g., 0.8) reduces false positives but may miss borderline content. Decreasing it increases sensitivity but may increase false positives.
