# Contributor Summary: Blackwell Support & Compatibility Fixes

This summary outlines the changes made to the 4DGaussians project to support the latest hardware and resolve dependency regressions.

## 1. Blackwell Architecture Support (SM 12.0 / 12.1)
The project now supports the NVIDIA Blackwell architecture (RTX 50-series).
- **Architecture Flags**: Added support for `SM 120` and `SM 121` in CUDA compilation environments.
- **Performance**: Verified training throughput on RTX 5070, matching or exceeding RTX 3090 benchmarks (~16.6 it/s on Lego dataset).
- **Environment**: Documented the necessary CUDA 12.x and PyTorch configurations for stable training on Blackwell.

## 2. Robust Configuration Loader (mmcv Fix)
Resolved a breaking change in the OpenMMLab dependency stack that prevented `render.py` from executing in many modern environments.
- **Change**: Updated the configuration import logic to handle both `mmengine` and `mmcv.Config`.
- **Value**: Ensures that the rendering pipeline is compatible with the latest version of these libraries, preventing `AttributeError: module 'mmcv' has no attribute 'Config'`.

## 3. Why These Changes Matter
- **Future-Proofing**: These fixes ensure the project runs on the next generation of consumer GPUs.
- **Stability**: Resolves common "out-of-the-box" crashes reported by users in the community when using modern Python environments.
