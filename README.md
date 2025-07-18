<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# GitHub Cheat Sheet for Beginners

This comprehensive guide covers everything you need to know about Git and GitHub, from basic commands to advanced troubleshooting techniques[^1_1].

## **Basic Git Commands**

### **Initial Setup**

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```


### **Repository Operations**

```bash
# Clone a repository
git clone https://github.com/username/repository.git

# Initialize a new repository
git init

# Check repository status
git status

# Add files to staging area
git add filename.txt          # Add specific file
git add .                     # Add all files
git add *.js                  # Add all JavaScript files

# Commit changes
git commit -m "Your commit message"

# Push changes to remote repository
git push origin branch-name

# Pull latest changes from remote
git pull origin branch-name
```


### **Branch Management**

```bash
# List all branches
git branch

# Create a new branch
git branch feature-branch-name

# Switch to a branch
git checkout feature-branch-name

# Create and switch to new branch in one command
git checkout -b feature-branch-name

# Delete a branch
git branch -d branch-name
```


## **Complete GitHub Workflow**

### **Step 1: Create Your Feature Branch Locally**

```bash
# Ensure you're on the main branch
git checkout main

# Pull latest changes
git pull origin main

# Create and switch to your feature branch
git checkout -b feature/user-authentication
```

**Visual Preview:**

```
main branch:     A---B---C---D
                          \
feature branch:            E (your new branch)
```


### **Step 2: Make Your Changes to Files**

```bash
# Edit your files using your preferred editor
# Then check what files have changed
git status

# View specific changes
git diff filename.txt

# Add changes to staging area
git add .

# Commit your changes
git commit -m "Add user authentication feature"
```

**Visual Preview:**

```
Working Directory → Staging Area → Local Repository
     (modified)   →   (git add)   →   (git commit)
```


### **Step 3: Push Your Branch to GitHub**

```bash
# Push your feature branch to GitHub
git push origin feature/user-authentication

# If it's your first push for this branch
git push -u origin feature/user-authentication
```

**Visual Preview:**

```
Local Repository → Remote Repository (GitHub)
                      (git push)
```


### **Step 4: Create a Pull Request**

1. Go to your repository on GitHub
2. Click "Compare \& pull request" button (appears after pushing)
3. Select base branch (usually `main` or `develop`)
4. Select compare branch (your feature branch)
5. Add title and description
6. Click "Create pull request"

**Visual Preview:**

```
GitHub Interface:
┌─────────────────────────────────────┐
│ base: main ← compare: feature/auth  │
│                                     │
│ Title: Add user authentication      │
│ Description: [Your detailed desc]   │
│                                     │
│ [Create pull request]               │
└─────────────────────────────────────┘
```


### **Step 5: Handle Conflicts (if any)**

If conflicts appear in the PR interface:

```bash
# Switch to your feature branch
git checkout feature/user-authentication

# Pull latest changes from main
git pull origin main

# Resolve conflicts in your editor
# Look for conflict markers: <<<<<<<, =======, >>>>>>>

# After resolving, add the resolved files
git add .

# Commit the merge
git commit -m "Resolve merge conflicts"

# Push the updated branch
git push origin feature/user-authentication
```

**Conflict Visual Preview:**

```
<<<<<<< HEAD (your changes)
const user = "John Doe";
=======
const user = "Jane Smith";
>>>>>>> main (incoming changes)
```


## **Emergency Commands for Common Blunders**

### **Wrong Merge Recovery**

```bash
# Undo last merge (if not pushed yet)
git reset --hard HEAD~1

# Undo merge that was already pushed
git revert -m 1 HEAD

# Reset to specific commit
git reset --hard commit-hash
```


### **Go Back to Previous State**

```bash
# See commit history
git log --oneline

# Reset to specific commit (destroys changes)
git reset --hard commit-hash

# Reset but keep changes in working directory
git reset --soft commit-hash

# Create new commit that undoes changes
git revert commit-hash
```


### **Fix Wrong Commit Message**

```bash
# Change last commit message (if not pushed)
git commit --amend -m "New commit message"

# If already pushed
git commit --amend -m "New commit message"
git push --force-with-lease origin branch-name
```


### **Recover Deleted Files**

```bash
# Restore file from last commit
git checkout HEAD -- filename.txt

# Restore file from specific commit
git checkout commit-hash -- filename.txt

# Restore all files to last commit state
git checkout HEAD -- .
```


### **Stash Changes Temporarily**

```bash
# Save work in progress
git stash

# Apply stashed changes
git stash pop

# List all stashes
git stash list

# Apply specific stash
git stash apply stash@{2}
```


### **Branch Management Emergencies**

```bash
# Switch branches with uncommitted changes
git stash
git checkout other-branch
git stash pop

# Rename current branch
git branch -m new-branch-name

# Delete remote branch
git push origin --delete branch-name
```


## **Advanced Troubleshooting**

### **Force Push (Use with Caution)**

```bash
# Force push (overwrites remote branch)
git push --force origin branch-name

# Safer force push (fails if others have pushed)
git push --force-with-lease origin branch-name
```


### **Interactive Rebase for Clean History**

```bash
# Rebase last 3 commits interactively
git rebase -i HEAD~3

# Common options in interactive rebase:
# pick = keep commit
# reword = change commit message
# squash = combine with previous commit
# drop = remove commit
```


### **Cherry-pick Specific Commits**

```bash
# Apply specific commit to current branch
git cherry-pick commit-hash

# Cherry-pick without committing
git cherry-pick -n commit-hash
```

**Visual Preview of Git Workflow:**

```
GitHub Remote Repository
         ↓ (git clone)
Local Repository
         ↓ (git checkout -b)
Feature Branch
         ↓ (make changes)
Working Directory
         ↓ (git add)
Staging Area
         ↓ (git commit)
Local Repository
         ↓ (git push)
GitHub Remote Repository
         ↓ (create PR)
Pull Request
         ↓ (merge)
Main Branch Updated
```

This cheat sheet provides a comprehensive foundation for Git and GitHub usage, from basic operations to emergency recovery techniques[^1_1]. Remember to always create backups and use `git status` frequently to understand your repository's current state.

<div style="text-align: center">⁂</div>

[^1_1]: programming.version_control