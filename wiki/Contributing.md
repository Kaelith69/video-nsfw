# Contributing

Thank you for your interest in contributing to `video-nsfw`! This guide covers the development workflow, code standards, and pull request process.

---

## Getting Started

### 1. Fork and Clone

```bash
# Fork via GitHub UI, then:
git clone https://github.com/YOUR_USERNAME/video-nsfw.git
cd video-nsfw
```

### 2. Set Up Development Environment

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
# .venv\Scripts\activate   # Windows

pip install -r requirements.txt
```

### 3. Create a Feature Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/issue-description
```

---

## Development Workflow

### Making Changes

- All application code lives in `video_analyzer.py`.
- Keep changes focused and minimal — one feature/fix per pull request.
- Follow the existing code style (see [Code Standards](#code-standards) below).

### Testing Your Changes

The project does not currently have an automated test suite. Before submitting a PR, manually verify:

1. The CLI works correctly on a test video:
   ```bash
   python video_analyzer.py /path/to/test_video.mp4
   ```

2. The Python API works as expected:
   ```python
   from video_analyzer import VideoContentAnalyzer
   analyzer = VideoContentAnalyzer()
   results = analyzer.analyze_video("test_video.mp4")
   print(results)
   ```

3. Error cases are handled:
   ```python
   # Should raise FileNotFoundError
   analyzer.analyze_video("nonexistent.mp4")
   ```

### Running a Quick Import Check

```bash
python -c "from video_analyzer import VideoContentAnalyzer; print('Import OK')"
```

---

## Code Standards

### Style

- Follow [PEP 8](https://peps.python.org/pep-0008/) for Python style.
- Use 4-space indentation (no tabs).
- Maximum line length: 100 characters.
- Use `snake_case` for variables, functions, and methods.
- Use `PascalCase` for class names.

### Type Hints

All public methods must have full type annotations:

```python
# Good
def analyze_frame(self, image: Image.Image) -> Tuple[str, float]:

# Bad
def analyze_frame(self, image):
```

### Docstrings

All classes and public methods must have docstrings following the existing format:

```python
def my_method(self, param: str) -> bool:
    """
    Brief description of what this method does.

    Parameters:
        param (str): Description of the parameter.

    Returns:
        bool: Description of the return value.
    """
```

### Logging

- Use `self.logger` (not `print`) for all diagnostic output.
- Use `INFO` for normal operational messages.
- Use `WARNING` for recoverable issues (e.g., failed frame reads).
- Use `ERROR` for conditions that prevent correct operation.

### Error Handling

- Raise standard Python exceptions (`FileNotFoundError`, `RuntimeError`, `ValueError`) with descriptive messages.
- Do not silence exceptions with bare `except:` clauses.
- Always use `try/finally` for external resources (file handles, etc.).

---

## Pull Request Process

### Before Submitting

- [ ] Code follows the style and standards above
- [ ] All public methods have type hints and docstrings
- [ ] Manual testing has been performed
- [ ] The CLI works correctly with a real video file
- [ ] No new dependencies have been added without discussion in an issue first
- [ ] Commit messages are clear and descriptive

### PR Title Format

```
<type>: <short description>

Types: feat, fix, docs, refactor, perf, test, chore
```

Examples:
- `feat: add batch video processing support`
- `fix: handle zero-frame videos without crashing`
- `docs: update installation instructions for Windows`
- `perf: reduce memory usage during frame sampling`

### PR Description

Include:
1. **What** — A concise description of the change
2. **Why** — The motivation or problem being solved
3. **How** — Key implementation decisions
4. **Testing** — How you verified the change

### Review Process

1. Open a PR against the `main` branch.
2. Address any review comments.
3. Once approved, the maintainer will merge.

---

## Reporting Bugs

Open a GitHub issue with:

- Python version (`python --version`)
- OS and version
- PyTorch version (`python -c "import torch; print(torch.__version__)"`)
- Steps to reproduce
- Expected behaviour
- Actual behaviour (including full error traceback)
- Video details (format, duration, resolution) if relevant

---

## Suggesting Features

Open a GitHub issue with:

- A clear description of the feature
- The use case / problem it solves
- Any relevant examples or references

---

## Code of Conduct

Be respectful and constructive in all interactions. This project follows the [Contributor Covenant](https://www.contributor-covenant.org/) code of conduct.
