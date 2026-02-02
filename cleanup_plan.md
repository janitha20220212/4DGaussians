# Project Cleanup & Blackwell Optimization Plan

The goal is to streamline the codebase and documentation to highlight the Blackwell GPU support and remove unnecessary clutter.

## Proposed Changes

### 1. File Cleanup
- **[DELETE]** `[16` and `[25`: Accidental artifact files.
- **[DELETE]** `output/test/smoke_blackwell`: Redundant initial test.
- **[DELETE]** `output/lego_test`, `output/lego_low_mem`: Empty or redundant experiment folders.
- **[DELETE]** `4DGaussians.ipynb`: If the user prefers a clean script-based focus, though keeping it as a reference might be useful. I will move it to a `docs/` folder or keep it.

### 2. Documentation Consolidation
- **[NEW] [README_BLACKWELL.md](file:///c:/Users/janit/OneDrive/Desktop/Janitha/IIT/FYP/4DGaussians%20-%20Copy/README_BLACKWELL.md)**: Combine `BLACKWELL_GUIDE.md`, `PERFORMANCE_ANALYSIS.md`, and `HARDWARE_COMPARISON.md` into one comprehensive guide.
- **[MODIFY] [README.md](file:///c:/Users/janit/OneDrive/Desktop/Janitha/IIT/FYP/4DGaussians%20-%20Copy/README.md)**: Update the intro to state that this repository is maintained for Blackwell GPUs.

### 3. Folder Organization
- Create a `docs/` or `support/` folder for the miscellaneous guides created if they clutter the root.

## Verification Plan
- Verify that the training and rendering still work with the primary `output/lego` iteration.
- Confirm all file links in the new consolidated README.
