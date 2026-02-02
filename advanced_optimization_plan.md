# Advanced Blackwell Optimization Plan

This plan outlines technical improvements to leverage the Blackwell architecture (SM 12.0/12.1) and modern PyTorch features to enhance training speed and rendering quality.

## User Review Required

> [!IMPORTANT]
> Some of these changes involve compiled components. If `torch.compile` is not supported by your specific hardware/driver version, it may fallback to standard execution with a slight startup delay.

## Proposed Changes

### Core Engine Optimization

#### [MODIFY] [deformation.py](file:///c:/Users/janit/OneDrive/Desktop/Janitha/IIT/FYP/4DGaussians%20-%20Copy/scene/deformation.py)
- Integrate `torch.compile(mode="reduce-overhead")` for the `Deformation` MLP and `query_time` methods.
- This will allow Blackwell's graph executor to optimize the neural network passes.

#### [MODIFY] [gaussian_model.py](file:///c:/Users/janit/OneDrive/Desktop/Janitha/IIT/FYP/4DGaussians%20-%20Copy/scene/gaussian_model.py)
- Implement **Adaptive Pruning Thresholds**: Instead of a static `min_opacity`, we will adjust it based on the point count to prevent memory overflow during long training runs on laptop 12GB VRAM.
- Optimize the `update_deformation_table` logic to use a more efficient tensor comparison.

### Submodule Enhancements

#### [MODIFY] [setup.py](file:///c:/Users/janit/OneDrive/Desktop/Janitha/IIT/FYP/4DGaussians%20-%20Copy/submodules/depth-diff-gaussian-rasterization/setup.py)
- Explicitly add `-gencode arch=compute_120,code=sm_120` to the nvcc flags to ensure the compiler uses Blackwell-specific instructions (like improved tensor core handling).

## Verification Plan

### Automated Tests
- Run a short 1000-iteration training test to verify `torch.compile` stability.
- Compare memory usage before and after adaptive pruning implementation.

### Manual Verification
- Check Tensorboard for smoother loss curves after implementing adaptive thresholds.
- Verify rendering FPS doesn't regress with compiled models.
