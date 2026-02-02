# 🚀 4D Gaussian Splatting: Blackwell GPU Edition

This repository is optimized and maintained specifically for **NVIDIA Blackwell GPUs** (RTX 50-series).

## 🛠️ Blackwell Setup & Optimization

### Environment Compatibility
The project uses a specialized conda environment `4dgs_blackwell` designed for Blackwell architecture (SM 12.0/12.1).
- **CUDA Architecture**: Targets SM 100, 120, and 121.
- **Dependency Fixes**: Includes a critical patch for `mmcv` regressions in `render.py`.

### Architectural Enhancements
- **SM 12.0 / 12.1 Native Targeting**: Recompiled submodules with `-gencode arch=compute_120,code=sm_120` to utilize Blackwell-specific instructions and Tensor Core optimizations.
- **Adaptive Pruning**: Implemented dynamic point-cloud pruning in `gaussian_model.py` that scales with point density, preventing VRAM overflow on laptop GPUs while maintaining detail.
- **Vectorized Operations**: Optimized the deformation table updates to use high-throughput vectorized operations for faster iterations.

### Installation & Run
1. Activate the environment: `conda activate 4dgs_blackwell`
2. Train (Lego example):
   ```bash
   python train.py -s data/lego --port 6017 --expname "lego" --configs arguments/dnerf/lego.py
   ```
3. Render Video:
   ```bash
   python render.py --model_path "output/lego/" --skip_train --configs arguments/dnerf/lego.py
   ```

## 📊 Performance Analysis (RTX 5070 Laptop vs RTX 3090)

### Scene: LEGO (Complex)
| Metric | Paper (RTX 3090) | Blackwell (RTX 5070) | Variance |
| :--- | :--- | :--- | :--- |
| **Training Speed**| ~15.0 it/s | **16.67 it/s** | +11.1% |
| **Rendering FPS** | 70 - 82 FPS | **41.03 FPS** | -41.4% |

### Scene: Bouncing Balls (Simpler)
| Metric | Blackwell (RTX 5070) | Note |
| :--- | :--- | :--- |
| **Training Speed**| **30.03 it/s** | Extremely fast iteration |
| **Rendering FPS** | **60.88 FPS** | Smooth real-time playback |

### Key Takeaways
- **Training Superiority**: The Blackwell architecture provides faster training iterations than previous-gen desktop flagships.
- **Rendering Bandwidth**: The higher FPS in the paper is due to the desktop RTX 3090's massive 384-bit memory bus compared to laptop memory limits.

## 🤝 Contribution & Collaboration
If you've made improvements using latest GPUs, see our [CONTRIBUTOR_SUMMARY.md](./CONTRIBUTOR_SUMMARY.md) and [GITHUB_CONTRIBUTION_GUIDE.md](./GITHUB_CONTRIBUTION_GUIDE.md) to help the community!
