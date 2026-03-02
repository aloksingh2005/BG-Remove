# BG-Remove (Background Remover)

> **⚡ Remove image backgrounds in seconds using AI—completely locally on your computer. No internet required after initial setup. No images uploaded anywhere.**

A modern, user-friendly desktop application to remove image backgrounds instantly. Built with **Python**, **CustomTkinter** for a sleek dark UI, **Pillow** for image handling, and **rembg** (powered by U²-Net) for AI-driven background removal.

**Perfect for:**
- Content creators, designers, e-commerce sellers
- Anyone needing quick background removal without online tools
- Privacy-conscious users (all processing stays on your machine)

---

## ✨ Features
- 🎨 **Clean Dark UI** – Modern, responsive interface using CustomTkinter
- 🖼️ **Live Preview** – See before/after side-by-side in real-time
- ⚡ **One-Click Removal** – Fast background removal with progress feedback
- 💾 **Easy Export** – Save transparent PNG with one click
- 🔄 **Multi-threaded** – UI stays responsive while processing large images
- 🏗️ **Standalone Build** – Create a Windows `.exe` and share with anyone (no Python needed!)
- 🔒 **100% Private** – All processing happens locally; nothing is uploaded

---

## 📋 Project Structure
```
BG-Remove/
├── app.py                 # Main GUI application (launch this!)
├── remove.py              # Standalone script example (optional)
├── app.spec               # PyInstaller config for .exe build
├── requirements.txt       # Python dependencies
└── README.md              # This file
```

---

## 🔧 Prerequisites

### **For Running the App (Both Paths)**
- **Windows 10/11** (project tested on Windows)
- **Python 3.10–3.12** installed on your computer
- **Internet connection** (only needed first time for downloading AI model)

> **🤔 Don't have Python? See "PATH A: Complete Beginner Setup" below.**

### **For Building a Windows .exe (Optional)**
- All of the above, plus `pyinstaller` (we'll install it)

---

## 🚀 Quick Start (3 Steps)

### **If you already know Python & virtual environments:**

```powershell
# 1. Clone or download this folder, then navigate to it
cd path/to/BG-Remove

# 2. Create virtual environment & install
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt

# 3. Run
python app.py
```

**Done!** The app opens with a GUI. Click "Select Image" and start removing backgrounds.

---

## 📖 Detailed Setup Instructions

Choose your path below:

---

### **PATH A: Complete Beginner Setup** ⭐
*No experience with Python or command line? Follow this step-by-step.*

#### **Step 1: Install Python (If Not Already Installed)**

1. Go to [python.org](https://www.python.org/downloads/)
2. Download **Python 3.11 or 3.12** (the latest versions)
3. Run the installer
   - ⚠️ **IMPORTANT:** Check **"Add Python to PATH"** during installation
   - Click "Install Now"
4. Wait for completion (2–3 minutes)

**Verify Python is installed:**
- Press `Win + R` on your keyboard
- Type `powershell` and press Enter (a blue terminal opens)
- Paste this and press Enter:
  ```powershell
  python --version
  ```
- You should see: `Python 3.11.x` or `Python 3.12.x`

> **If you see "python is not recognized":** Python isn't in your PATH. Reinstall and make sure to check "Add Python to PATH."

---

#### **Step 2: Download & Navigate to Project**

1. **Download this project:**
   - Click the green "Code" button on GitHub → "Download ZIP"
   - OR clone it if you know Git
   - Extract the folder to a convenient location (e.g., Desktop or Documents)

2. **Open Terminal in Project Folder:**
   - Navigate to the extracted `BG-Remove` folder
   - Hold `Shift` and right-click inside the folder → "Open PowerShell window here"
   - A blue terminal should appear

3. **Verify you're in the right place:**
   - You should see your current path ends with `...BG-Remove>`
   - You should see files: `app.py`, `requirements.txt`, `README.md`

---

#### **Step 3: Create Virtual Environment** (Recommended but Optional)

*A virtual environment keeps Python dependencies for this project separate from other projects.*

In the PowerShell terminal, copy-paste this command and press Enter:

```powershell
python -m venv .venv
```

**Expected output:**
```
(nothing—it just creates a folder named .venv)
```

---

#### **Step 4: Activate Virtual Environment**

Still in PowerShell, run:

```powershell
.\.venv\Scripts\Activate.ps1
```

**Expected output:**
```
(.venv) C:\Users\YourName\...\BG-Remove>
```

Notice the `(.venv)` at the beginning—that means it's activated! ✅

> **If you get an error about "execution policies":**
> ```powershell
> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
> ```
> Then run the activation command again.

---

#### **Step 5: Install Dependencies**

Still in the terminal (with `.venv` activated), run:

```powershell
pip install -r requirements.txt
```

**Expected output** *(you'll see lots of lines)*:
```
Collecting rembg>=0.0.51
  Downloading rembg-0.0.51-py3-none-any.whl ...
Collecting pillow>=9.0.0
  Downloading Pillow-9.5.0-cp311-cp311-win_amd64.whl ...
...
Successfully installed rembg-0.0.51 pillow-9.5.0 customtkinter-5.0 onnxruntime-1.14.0 numba-0.56.0
```

This takes **2–5 minutes** depending on your internet speed. The first run might be slower.

---

#### **Step 6: Run the App! 🎉**

Still in the terminal, run:

```powershell
python app.py
```

**Expected output:**
```
Initializing app...
```

A **large window with a dark background** should appear. This is the BG-Remove app!

---

### **PATH B: Developer Quick Start**
*You know Python, virtual environments, and want to skip hand-holding.*

```powershell
# In your project directory:
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```

Done. Enjoy!

---

## 📱 Using the App (GUI)

Once the app is running:

1. **Click "Select Image"**
   - Choose any `.png`, `.jpg`, `.jpeg`, `.bmp`, or `.gif`
   - The original image appears on the left side

2. **Click "Remove Background"**
   - You'll see a progress bar at the bottom
   - Once complete, the processed image (with transparent background) appears on the right
   - ⏱️ Time depends on image size (typically 5–30 seconds)

3. **Click "Save Image"**
   - Choose where to save your transparent PNG
   - Done! Open it in any image editor

> **💡 Pro Tip:** Test with small images first (512×512) to see how fast it is.

---

## 🐍 Using the Script (Optional)

If you want to use background removal in your own Python code, see `remove.py`:

```python
from rembg import remove
from PIL import Image

# Open image
input_image = Image.open("photo.jpg")

# Remove background
output_image = remove(input_image)

# Save transparent PNG
output_image.save("photo_transparent.png")
```

---

## 🏗️ Building a Windows .exe (Standalone App)

### **Why Build an .exe?**
- Share the app with others who don't have Python installed
- Easy to use (just double-click)
- Portable (no dependencies needed on the target machine)

### **How to Build**

#### **Step 1: Install PyInstaller**
With your virtual environment activated:
```powershell
pip install pyinstaller
```

#### **Step 2: Build the Executable**
Still in your project folder:

```powershell
pyinstaller app.spec
```

**Expected output:**
```
... (lots of lines)
1254 INFO: Bootloader C:\Users\...\pyinstaller\bootloader\...
Building EXE from EXE-00.toc completed successfully.
```

#### **Step 3: Find Your .exe**

Navigate to the `dist/app/` folder in your project. You'll find:
```
dist/
└── app/
    ├── app.exe              ← This is your executable!
    ├── api-ms-win-core-...   (helper files)
    ├── customtkinter.pyd
    ├── _bz2.pyd
    └── (many other .pyd files)
```

#### **Step 4: Share or Run**

- **To run locally:** Double-click `dist/app/app.exe`
- **To share with others:** Zip the entire `dist/app/` folder and send it
  - On their machine, they just extract and double-click `app.exe`
  - No Python installation needed! ✨

### **Build Optimization Notes**
- **File size:** Typically 200–400 MB (depends on Windows & Python version)
- **First run:** Model weights are downloaded (~500 MB) on first use
- **Speed:** Nearly identical to running with `python app.py`
- **UPX compression:** The spec enables it if installed; ignore if unavailable

---

## ⚠️ Troubleshooting

### **Problem: "Python is not recognized"**
**Solution:**
1. Python isn't installed or not in PATH
2. Reinstall Python from [python.org](https://www.python.org/downloads/)
3. ⚠️ **Check "Add Python to PATH" during installation**
4. Restart your terminal after reinstalling

---

### **Problem: Virtual Environment Won't Activate**
**Symptom:** PowerShell error about "execution policies"

**Solution:**
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Then try again:
```powershell
.\.venv\Scripts\Activate.ps1
```

---

### **Problem: "DLL load failed" when running app.py**
**Symptom:**
```
RuntimeError: Failed to load ONNX model
OSError: [WinError 127] The specified procedure could not be found
```

**Solutions (try in order):**

1. **Reinstall onnxruntime:**
   ```powershell
   pip uninstall onnxruntime
   pip install onnxruntime==1.18.0
   ```

2. **Update your OS:**
   - Install the latest Windows updates
   - Restart your computer
   - Try running the app again

3. **Check Windows version:**
   - Press `Win + R` → type `winver` → press Enter
   - Ensure you're on Windows 10 (Build 1909+) or Windows 11
   - Older builds may not support required DLLs

4. **Try an older Python version:**
   - Some Windows 10 systems work better with Python 3.10
   - Reinstall Python and use Python 3.10 instead

---

### **Problem: App Doesn't Open (Black Window Appears Then Closes)**
**Solution:**
1. Open PowerShell in your project folder
2. Activate `.venv`
3. Run:
   ```powershell
   python app.py
   ```
4. Look for error messages in the terminal
5. Share the error message if still stuck

---

### **Problem: "No module named 'rembg'" or Similar Import Error**
**Symptom:**
```
ModuleNotFoundError: No module named 'rembg'
```

**Solution:**
1. Make sure virtual environment is activated (see `(.venv)` prefix)
2. Reinstall dependencies:
   ```powershell
   pip install -r requirements.txt
   ```
3. Try again

---

### **Problem: Processing Takes Very Long (>2 minutes)**
**Causes & Solutions:**
- **Large image (3000×3000+):** Processing scales with image size
  - Resize your image before processing (aim for 800×600 max)
  
- **Low disk space:** Not enough RAM or disk
  - Close other apps
  - Free up disk space
  
- **Weak PC:** Background removal is CPU/GPU intensive
  - First run takes longer (downloads 500 MB model)
  - Subsequent runs are faster

---

### **Problem: Building .exe Fails**
**Symptom:**
```
PyInstallerHooks or compilation errors
```

**Solution:**
1. Make sure all dependencies are installed:
   ```powershell
   pip install -r requirements.txt
   pip install pyinstaller
   ```
2. Try the simple build:
   ```powershell
   pyinstaller --noconsole --name app app.py
   ```
3. If that works, your custom spec has an issue
4. Use the simpler build command above

---

### **Problem: .exe Crashes When I Try to Use It**
**Solution:**
1. Run `.exe` from PowerShell terminal to see error messages:
   ```powershell
   .\dist\app\app.exe
   ```
2. Share the error message
3. Ensure all dependencies are in your virtual environment

---

## 📊 What Each File Does

| File | Purpose |
|------|---------|
| `app.py` | Main GUI application (launch this!) |
| `remove.py` | Standalone example: shows how to use `rembg` in Python script |
| `app.spec` | PyInstaller configuration for building `.exe` |
| `requirements.txt` | List of Python libraries needed |
| `README.md` | This file |

---

## 📦 Dependencies Explained

| Package | Why It's Needed | Size |
|---------|-----------------|------|
| **rembg** | AI model for background removal | ~50 MB |
| **customtkinter** | Modern UI toolkit (dark theme) | ~10 MB |
| **pillow** | Image loading and manipulation | ~5 MB |
| **onnxruntime** | Runs the AI model efficiently | ~30 MB |
| **numba** | Speed up numerical computations | ~10 MB |

**Total environment size:** ~150 MB + Python

---

## 🔒 Privacy & Security

✅ **All processing happens on your computer**
- No images are uploaded anywhere
- No tracking or telemetry
- Works offline after first setup (model is cached locally)
- Completely safe for sensitive images

---

## 📝 License

This project is provided as-is.

**Licenses of included libraries:**
- `rembg`: MIT License
- `customtkinter`: MIT License
- `pillow`: HPND License
- `onnxruntime`: MIT License
- Models (U²-Net): Apache 2.0 License

See original repositories for full license details.

---

## 🙏 Acknowledgments

- [`rembg`](https://github.com/danielgatis/rembg) – Amazing background removal library
- [`customtkinter`](https://github.com/TomSchimansky/CustomTkinter) – Modern Python UI toolkit
- [`ONNX`](https://onnx.ai/) – Model format and runtime
- [`U²-Net`](https://github.com/xuebinqin/U-2-Net) – Original segmentation model

---

## 🤝 Support

Having issues?
1. Check **Troubleshooting** section above
2. Ensure you followed PATH A or PATH B completely
3. Share your error messages when asking for help

---

**Made with ❤️ for creators, designers, and privacy-conscious users.**
