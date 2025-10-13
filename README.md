# BG-Remove (Background Remover)

A simple, modern desktop app to remove image backgrounds locally using AI. Built with Python, CustomTkinter for a clean UI, Pillow for image handling, and `rembg` (U^2-Net via ONNXRuntime) for background removal. Includes a ready-to-build PyInstaller spec for producing a Windows `.exe`.

## Features
- Clean dark UI using CustomTkinter
- Load, preview, and compare original vs processed images
- One-click background removal with progress feedback
- Save transparent PNG output
- Multithreaded processing to keep the UI responsive
- Standalone Windows build via PyInstaller (`app.spec`)

## Project Structure
- `app.py`: GUI application (main entry point)
- `remove.py`: Minimal CLI-style example for background removal
- `app.spec`: PyInstaller spec to build a windowed executable
- `requirements.txt`: Python dependencies
- `dist/`, `build/`: Output directories created by PyInstaller

## Prerequisites
- Windows 10/11 (project tested on Windows)
- Python 3.10–3.12 recommended
- (Optional) Virtual environment

## Setup
```bash
# 1) Create and activate a virtual environment (Windows PowerShell)
python -m venv my_env
./my_env/Scripts/Activate.ps1

# 2) Upgrade pip and install dependencies
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If ONNXRuntime installation fails on your machine, try:
```bash
pip install onnxruntime==1.18.0
```

## Run (GUI)
```bash
# From project root with venv activated
python app.py
```
- Click "Select Image" to choose an image (`.png`, `.jpg`, `.jpeg`, `.bmp`, `.gif`).
- Click "Remove Background" to process.
- Click "Save Image" to export as a transparent `.png`.

## Run (Script Example)
`remove.py` demonstrates background removal in a few lines:
```python
from rembg import remove
from PIL import Image

image_input = Image.open("input.jpg")
output = remove(image_input)
output.save("output.png")
```

## Build a Windows Executable
This project includes a PyInstaller spec (`app.spec`) already configured for a windowed build.

```bash
# Ensure venv is active and deps installed
pip install pyinstaller

# Option A: Build from spec (recommended)
pyinstaller app.spec

# Option B: Build directly
pyinstaller --noconsole --name app app.py
```

- Outputs:
  - `dist/app/app.exe` (portable executable)
  - `build/` (intermediate files)

### Common Build Notes
- If the UI doesn’t launch or EXE crashes, ensure these packages exist in your venv: `customtkinter`, `pillow`, `rembg`, `onnxruntime`.
- For smaller binaries, you can experiment with UPX. The spec enables UPX by default if installed.
- On first run, `rembg` may download model weights; ensure internet access or prefetch models as needed.

## Troubleshooting
- "DLL load failed" on `onnxruntime`:
  - Ensure you’re on a supported Python and Windows version.
  - Try `pip install onnxruntime==1.18.0`.
- Black window or app not opening:
  - Run from terminal to view errors: `python app.py`.
- Very large images render slowly:
  - The app thumbnails to keep the UI snappy, but background removal runtime scales with image size.

## Notes on Privacy
All processing happens locally on your machine. No images are uploaded.

## License
This project is provided as-is. Models and libraries (`rembg`, ONNXRuntime, etc.) are subject to their respective licenses.

## Acknowledgments
- [`rembg`](https://github.com/danielgatis/rembg)
- [`CustomTkinter`](https://github.com/TomSchimansky/CustomTkinter)
- [`Pillow`](https://python-pillow.org)
- [`PyInstaller`](https://pyinstaller.org)
