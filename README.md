# Git Merge Conflicts Workshop

A simple Python calculator application designed to demonstrate git merge conflict resolution.

## Prerequisites

- Git installed
- Python installed
- Basic understanding of git commands (commit, branch, merge)

## Workshop Setup

### Step 1: Initial Setup

1. Clone this repository (if working from remote):
   ```bash
   git clone <repository-url>
   cd SE-merge-conflict
   ```

2. Fetch all branches from the remote:
   ```bash
   git fetch origin
   ```

3. Pull all branches to create local tracking branches:
   ```bash
   git checkout feature-power
   git checkout feature-modulo
   git checkout main-browser
   git checkout feature-power-browser
   git checkout feature-modulo-browser
   git checkout main
   ```
   
   Note: When you checkout a remote branch for the first time, git automatically creates a local tracking branch.

4. Verify the initial state:
   ```bash
   git log --oneline
   git branch
   ```

### Step 2: Explore the Branches

This repository contains several branches:

**Command-line demo branches:**
- `feature-power` branch that adds a power operation
- `feature-modulo` branch that adds a modulo operation
- Both branches modify the same sections of code, creating merge conflicts

**Browser demo branches (for GitHub web interface):**
- `main-browser` - exact copy of main
- `feature-power-browser` - adds power operation
- `feature-modulo-browser` - adds modulo operation

You can view all available branches:
```bash
git branch -a
```

### Step 3: Experience the Conflict

1. Switch to the `feature-power` branch:
   ```bash
   git checkout feature-power
   ```
   Review the changes made in this branch.

2. Switch back to `main`:
   ```bash
   git checkout main
   ```

3. Merge `feature-power`:
   ```bash
   git merge feature-power
   ```
   This should merge successfully.

4. Now try to merge `feature-modulo`:
   ```bash
   git merge feature-modulo
   ```
   **This will create merge conflicts!**

### Step 4: Resolve the Conflicts

1. Open `calculator.py` in your editor. You'll see conflict markers:
   ```
   <<<<<<< HEAD
   (code from feature-power)
   =======
   (code from feature-modulo)
   >>>>>>> feature-modulo
   ```

2. Resolve the conflicts by:
   - Keeping both features (power and modulo)
   - Removing the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
   - Ensuring the code is correct and complete

3. Stage the resolved file:
   ```bash
   git add calculator.py
   ```

4. Complete the merge:
   ```bash
   git commit
   ```
   (Git will open an editor with a default merge commit message)

### Step 5: Verify the Resolution

1. Test the calculator:
   ```bash
   python calculator.py
   ```

2. Verify all operations work:
   - Addition (+)
   - Subtraction (-)
   - Multiplication (*)
   - Division (/)
   - Power (^)
   - Modulo (%)

## Troubleshooting

### Reset to Start Over

If you want to start fresh:
```bash
git checkout main
git reset --hard HEAD
git clean -fd
```

Note: The branches are already set up in the repository. If you've made changes and want to reset, you may need to fetch the original branches again.

### View Conflict Details

To see what's conflicting:
```bash
git status
git diff
```