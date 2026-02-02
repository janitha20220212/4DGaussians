# GitHub Contribution Guide (Beginner Friendly)

Since you've improved the code for Blackwell GPUs, contributing back to the original repository is a great way to build your profile as a developer. Here is the process:

## Step 1: Fork the Repository
1. Go to the [original 4DGaussians repository](https://github.com/hustvl/4DGaussians).
2. Click the **Fork** button (top right) to create your own copy on GitHub.

## Step 2: Clone & Apply Changes
If you have already made changes locally (which we have), you can just link your local folder to your fork:
1. Initialize Git in your folder if you haven't: `git init`
2. Connect to your fork: `git remote add origin https://github.com/YOUR_USERNAME/4DGaussians.git`

## Step 3: Create a Branch
Always make changes on a separate branch, never on `main`.
```bash
git checkout -b feature/blackwell-support
```

## Step 4: Commit & Push
```bash
git add .
git commit -m "Add support for Blackwell GPUs and fix mmcv config error"
git push origin feature/blackwell-support
```

## Step 5: Start a Pull Request (PR)
1. Go to your fork on GitHub.
2. You will see a button: **"Compare & Pull Request"**. Click it.
3. Use the content from [CONTRIBUTOR_SUMMARY.md](./CONTRIBUTOR_SUMMARY.md) to fill out the description.

## Tips for a Great PR
- **Screenshots**: If you can, attach a screenshot of your successful training or the rendered video.
- **Be Polite**: Mention that you are using an RTX 50-series card and noticed these fixes were needed.
- **Follow Up**: The maintainers might ask questions; try to respond within a few days.

*Good luck with your first contribution!*
