# Version Control Guide (Git)

This project uses **Git** for version control. Here is how you can manage your changes and maintain different versions of the project.

## Basic Setup

If you haven't initialized the repository or want to check the status:
```bash
# Check the current status of your files
git status

# See what changes you have made
git diff
```

## Daily Workflow (Version Control)

### 1. Staging Changes
When you make a change (like the Blackwell GPU fixes), you should stage them:
```bash
# Add specific files
git add render.py BLACKWELL_GUIDE.md

# Or add all changes
git add .
```

### 2. Committing Changes
Create a snapshot of your work:
```bash
git commit -m "Add Blackwell GPU support and patch mmcv dependency"
```

### 3. Branching (Experimental Work)
If you want to try something risky without breaking the main training code:
```bash
# Create and switch to a new branch
git checkout -b experimental_feature

# List all branches
git branch
```

## Recommended Best Practices
- **Commit often**: Small, atomic commits are easier to track and revert if needed.
- **Meaningful messages**: Describe "why" you made the change, not just "what" changed.
- **Use .gitignore**: Ensure large files like `.mp4` or `.pth` (weights) are not tracked unless necessary, to keep the repo size small.
