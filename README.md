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

2. Run the setup script to create the workshop branches:
   ```bash
   python setup_workshop.py
   ```
   The script creates `feature-power`, `feature-modulo`, and browser branches (`main-browser`, `feature-power-browser`, `feature-modulo-browser`) from the current repo state.

3. Optionally verify the setup:
   ```bash
   git log --oneline
   git branch
   ```

### Step 2: Experience the Conflict

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

### Step 3: Resolve the Conflicts

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

### Step 4: Verify the Resolution

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

If you want to start fresh, run the setup script again. When prompted, choose to delete and recreate the branches:
```bash
python setup_workshop.py
```
Answer `y` when asked "Branches already exist. Delete and recreate?"

### View Conflict Details

To see what's conflicting:
```bash
git status
git diff
```