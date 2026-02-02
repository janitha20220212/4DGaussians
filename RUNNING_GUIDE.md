# 🏃 Running Guide: 4D Gaussian Splatting

This guide will walk you through the process of setting up, training, and rendering your first 4D Gaussian scene, specifically optimized for Blackwell GPUs.

## 1. Environment Setup
Before running any scripts, you must activate the Blackwell-optimized environment.

```bash
# Open your terminal and run:
conda activate 4dgs_blackwell
```

## 2. Data Preparation
Ensure your data is organized in the `data/` folder. For the Lego dataset:
- Path: `data/lego/`
- Structure: Should contain `train/`, `test/`, and `val/` folders with image sequences and camera parameters.

## 3. Training the Model
Training creates the 4D Gaussian represention from your images.

```bash
# Basic Training Command
python train.py -s data/lego --port 6017 --expname "lego" --configs arguments/dnerf/lego.py
```
- `-s`: Path to the source data.
- `--expname`: The name of your experiment (outputs will be saved in `output/<expname>`).
- `--configs`: The architectural configuration file for the specific dataset.

**Note**: On Blackwell hardware, training for 20,000 iterations typically takes **~11-15 minutes**.

## 4. Rendering Video
Once training is finished, you can generate a video from the trained model.

```bash
# Rendering Command
python render.py --model_path "output/lego/" --skip_train --configs arguments/dnerf/lego.py
```
- `--model_path`: Path where the trained model is saved.
- `--skip_train`: Skips rendering the training set (saves time).
- Output: Your final video will be at `output/lego/video/ours_20000/video_rgb.mp4`.

## 5. Troubleshooting
- **Out of Memory (OOM)**: If the GPU runs out of memory, try using a smaller dataset or decreasing the resolution in the config file.
- **Dependency Errors**: Ensure you have patched `render.py` (which we have already done) to avoid `mmcv` attribute errors.
- **Port Busy**: If port `6017` is in use, change it to another number like `6018`.

---
*Maintained for Blackwell GPUs (RTX 50-series).*
