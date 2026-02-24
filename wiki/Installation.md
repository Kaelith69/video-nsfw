# Installation

This page covers all supported installation scenarios for `video-nsfw`.

---

## Prerequisites

| Requirement | Minimum Version | Notes |
|---|---|---|
| Python | 3.9 | 3.10+ recommended |
| pip | 21.0+ | Pre-installed with modern Python |
| Git | any | For cloning the repository |
| CUDA Toolkit | 11.8+ | Optional; required only for GPU acceleration |

---

## Standard Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Kaelith69/video-nsfw.git
cd video-nsfw
```

### 2. Create a Virtual Environment (Recommended)

**Linux / macOS:**

```bash
python -m venv .venv
source .venv/bin/activate
```

**Windows (PowerShell):**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**Windows (Command Prompt):**

```cmd
python -m venv .venv
.venv\Scripts\activate.bat
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

This installs:

| Package | Minimum Version |
|---|---|
| `opencv-python` | 4.8.0 |
| `torch` | 2.0.0 |
| `Pillow` | 10.0.0 |
| `transformers` | 4.35.0 |

### 4. Verify Installation

```bash
python -c "
import cv2
import torch
from PIL import Image
from transformers import AutoModelForImageClassification
print('OpenCV:', cv2.__version__)
print('PyTorch:', torch.__version__)
print('CUDA available:', torch.cuda.is_available())
print('All dependencies OK')
"
```

---

## GPU Installation (CUDA)

To use GPU acceleration, replace the default `torch` installation with a CUDA-enabled build.

### CUDA 12.1 (Recommended for modern GPUs)

```bash
pip install torch --index-url https://download.pytorch.org/whl/cu121
pip install opencv-python>=4.8.0 Pillow>=10.0.0 transformers>=4.35.0
```

### CUDA 11.8

```bash
pip install torch --index-url https://download.pytorch.org/whl/cu118
pip install opencv-python>=4.8.0 Pillow>=10.0.0 transformers>=4.35.0
```

### Verify GPU Detection

```bash
python -c "import torch; print('CUDA available:', torch.cuda.is_available()); print('GPU:', torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'N/A')"
```

---

## Model Download

On the first run, the `Falconsai/nsfw_image_detection` model weights (~85 MB) are automatically downloaded from HuggingFace Hub and cached:

- **Linux/macOS:** `~/.cache/huggingface/hub/`
- **Windows:** `%USERPROFILE%\.cache\huggingface\hub\`

Subsequent runs use the local cache — no internet connection is required after the first run.

### Pre-downloading the Model

To download the model before running (e.g., for air-gapped environments):

```python
from transformers import AutoModelForImageClassification, ViTImageProcessor
AutoModelForImageClassification.from_pretrained("Falconsai/nsfw_image_detection")
ViTImageProcessor.from_pretrained("Falconsai/nsfw_image_detection")
print("Model cached successfully")
```

### Using a Local Model

If you have a local copy of the model (downloaded directory), pass its path to the constructor:

```python
from video_analyzer import VideoContentAnalyzer
analyzer = VideoContentAnalyzer(model_name="/path/to/local/model")
```

---

## Platform-Specific Notes

### Linux

No platform-specific steps required. All packages are available via pip.

### macOS

- Apple Silicon (M1/M2/M3): PyTorch supports Metal Performance Shaders (MPS) acceleration. Automatic device selection currently uses CPU; MPS support may be added in future versions.
- Intel Mac: CPU inference works out of the box.

### Windows

- Ensure Visual C++ Redistributable is installed (required by OpenCV).
- Use PowerShell or Command Prompt — not Git Bash — for virtual environment activation.
- Long path support (`HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\LongPathsEnabled = 1`) is recommended to avoid pip installation issues.

---

## Docker Installation

A minimal `Dockerfile` for containerised deployment:

```dockerfile
FROM python:3.11-slim

WORKDIR /app

# Install system dependencies for OpenCV
RUN apt-get update && apt-get install -y \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgl1-mesa-glx \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY video_analyzer.py .

# Pre-cache the model
RUN python -c "from transformers import AutoModelForImageClassification, ViTImageProcessor; \
    AutoModelForImageClassification.from_pretrained('Falconsai/nsfw_image_detection'); \
    ViTImageProcessor.from_pretrained('Falconsai/nsfw_image_detection')"

ENTRYPOINT ["python", "video_analyzer.py"]
```

Build and run:

```bash
docker build -t video-nsfw .
docker run --rm -v /path/to/videos:/data video-nsfw /data/my_video.mp4
```

---

## Uninstalling

```bash
# Deactivate and remove the virtual environment
deactivate
rm -rf .venv

# Remove the HuggingFace model cache (optional)
rm -rf ~/.cache/huggingface/hub/models--Falconsai--nsfw_image_detection
```
