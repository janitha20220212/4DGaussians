# Contributing to 4DGaussians (Blackwell Optimized)

Since you've improved the code for Blackwell GPUs, contributing back to the original repository is a great way to build your profile as a developer.

## Changes Included in this Version

### 1. Blackwell Architecture Support (SM 12.0 / 12.1)
The project now supports the NVIDIA Blackwell architecture (RTX 50-series).
- **Architecture Flags**: Added support for `SM 120` and `SM 121` in CUDA compilation environments.
- **Performance**: Verified training throughput on RTX 5070, matching or exceeding RTX 3090 benchmarks (~16.6 it/s on Lego dataset).
- **Environment**: Documented the necessary CUDA 12.x and PyTorch configurations for stable training on Blackwell.

### 2. Robust Configuration Loader (mmcv Fix)
Resolved a breaking change in the OpenMMLab dependency stack that prevented `render.py` from executing in many modern environments.
- **Change**: Updated the configuration import logic to handle both `mmengine` and `mmcv.Config`.
- **Value**: Ensures that the rendering pipeline is compatible with the latest version of these libraries, preventing `AttributeError: module 'mmcv' has no attribute 'Config'`.

## Contribution Process

### Step 1: Fork the Repository
1. Go to the [original 4DGaussians repository](https://github.com/hustvl/4DGaussians).
2. Click the **Fork** button (top right) to create your own copy on GitHub.

### Step 2: Clone & Apply Changes
1. Initialize Git in your folder if you haven't: `git init`
2. Connect to your fork: `git remote add origin https://github.com/YOUR_USERNAME/4DGaussians.git`

### Step 3: Create a Branch
```bash
git checkout -b feature/blackwell-support
```

### Step 4: Commit & Push
```bash
git add .
git commit -m "Add support for Blackwell GPUs and fix mmcv config error"
git push origin feature/blackwell-support
```

### Step 5: Start a Pull Request (PR)
1. Go to your fork on GitHub.
2. Click **"Compare & Pull Request"**.
3. Use the summary of changes above to fill out the description.

## Tips for a Great PR
- **Screenshots**: Attach screenshots of successful training or the rendered video.
- **Be Polite**: Mention you are using an RTX 50-series card.
- **Follow Up**: Respond to maintainer questions promptly.
