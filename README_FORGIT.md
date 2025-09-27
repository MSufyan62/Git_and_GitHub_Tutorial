# Git Commands Reference Guide

## 📚 Complete Git Commands Cheat Sheet

### 🚀 Getting Started with Git

#### Initial Setup

```bash
# Set your name and email (required for commits)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Check current configuration
git config --list

# Get help for any git command
git help <command>
```

### 📁 Repository Management

#### Creating & Cloning Repositories

```bash
# Initialize a new local repository
git init

# Clone a remote repository
git clone <repository-url>

# Clone to a specific directory
git clone <repository-url> <directory-name>
```

### 📝 Basic Workflow Commands

#### Checking Status & Adding Files

```bash
# Check repository status
git status

# Add specific file to staging area
git add <filename>

# Add all files to staging area
git add .

# Add all files with specific extension
git add *.txt

# Remove file from staging area
git reset <filename>
```

#### Committing Changes

```bash
# Commit staged changes with message
git commit -m "Your commit message"

# Commit all tracked files (skip staging)
git commit -am "Your commit message"

# Amend the last commit
git commit --amend -m "Updated commit message"
```

### 🌿 Branch Management

#### Creating & Switching Branches

```bash
# List all branches
git branch

# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>

# Create and switch to new branch
git checkout -b <branch-name>

# Delete a branch
git branch -d <branch-name>

# Force delete a branch
git branch -D <branch-name>

# Rename current branch
git branch -m <new-branch-name>
```

#### Merging Branches

```bash
# Merge branch into current branch
git merge <branch-name>

# Merge with no fast-forward
git merge --no-ff <branch-name>

# Abort a merge in progress
git merge --abort
```

### 🔄 Remote Repository Operations

#### Working with Remotes

```bash
# List remote repositories
git remote -v

# Add a remote repository
git remote add <remote-name> <repository-url>

# Remove a remote
git remote remove <remote-name>

# Rename a remote
git remote rename <old-name> <new-name>
```

#### Pushing & Pulling

```bash
# Push to remote repository
git push <remote-name> <branch-name>

# Push and set upstream branch
git push -u <remote-name> <branch-name>

# Push all branches
git push --all

# Pull changes from remote
git pull <remote-name> <branch-name>

# Fetch changes without merging
git fetch <remote-name>

# Pull with rebase
git pull --rebase
```

### 📖 History & Information

#### Viewing Commit History

```bash
# View commit history
git log

# View compact log
git log --oneline

# View log with graph
git log --graph --oneline --all

# View specific number of commits
git log -n 5

# View commits by author
git log --author="Author Name"

# View commits for specific file
git log <filename>
```

#### Comparing Changes

```bash
# Show changes in working directory
git diff

# Show changes in staging area
git diff --staged

# Compare two branches
git diff <branch1> <branch2>

# Compare specific commits
git diff <commit1> <commit2>
```

### ⏪ Undoing Changes

#### Resetting & Reverting

```bash
# Discard changes in working directory
git checkout -- <filename>

# Reset to last commit (keep changes in working directory)
git reset --soft HEAD~1

# Reset to last commit (discard changes)
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard <commit-hash>

# Revert a commit (creates new commit)
git revert <commit-hash>
```

#### Stashing Changes

```bash
# Stash current changes
git stash

# Stash with message
git stash save "Work in progress"

# List all stashes
git stash list

# Apply most recent stash
git stash apply

# Apply and remove stash
git stash pop

# Drop a stash
git stash drop <stash@{n}>

# Clear all stashes
git stash clear
```

### 🏷️ Tags

#### Working with Tags

```bash
# List all tags
git tag

# Create a lightweight tag
git tag <tag-name>

# Create an annotated tag
git tag -a <tag-name> -m "Tag message"

# Push tags to remote
git push origin <tag-name>

# Push all tags
git push origin --tags

# Delete a tag locally
git tag -d <tag-name>

# Delete a tag on remote
git push origin --delete <tag-name>
```

### 🔧 Advanced Commands

#### Rebasing

```bash
# Rebase current branch onto another branch
git rebase <branch-name>

# Interactive rebase (last n commits)
git rebase -i HEAD~n

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort
```

#### Cherry Picking

```bash
# Apply specific commit to current branch
git cherry-pick <commit-hash>

# Cherry pick multiple commits
git cherry-pick <commit1> <commit2>
```

### 🛠️ Useful Shortcuts & Tips

#### Aliases (Add to your git config)

```bash
# Create useful aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.lg "log --oneline --graph --all"
```

#### Common Patterns

```bash
# Quick commit all changes
git add . && git commit -m "Quick update"

# Push current branch to origin
git push origin HEAD

# Create and push new branch
git checkout -b feature/new-feature && git push -u origin feature/new-feature

# Sync with remote main branch
git checkout main && git pull origin main
```

### 🚨 Emergency Commands

#### When Things Go Wrong

```bash
# Undo last commit but keep changes
git reset HEAD~1

# Completely reset to remote state
git fetch origin && git reset --hard origin/main

# Recover deleted branch (if you know last commit)
git checkout -b <branch-name> <commit-hash>

# Find lost commits
git reflog
```

### 📊 Git Workflow Examples

#### Feature Branch Workflow

```bash
# 1. Start from main branch
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b feature/awesome-feature

# 3. Make changes and commit
git add .
git commit -m "Add awesome feature"

# 4. Push feature branch
git push -u origin feature/awesome-feature

# 5. After code review, merge to main
git checkout main
git merge feature/awesome-feature
git push origin main

# 6. Clean up
git branch -d feature/awesome-feature
git push origin --delete feature/awesome-feature
```

#### Hotfix Workflow

```bash
# 1. Create hotfix branch from main
git checkout main
git checkout -b hotfix/critical-bug-fix

# 2. Make the fix and commit
git add .
git commit -m "Fix critical bug in production"

# 3. Merge back to main
git checkout main
git merge hotfix/critical-bug-fix
git push origin main

# 4. Tag the release
git tag -a v1.0.1 -m "Hotfix release v1.0.1"
git push origin v1.0.1

# 5. Clean up
git branch -d hotfix/critical-bug-fix
```

### 🔍 Advanced Git Commands

#### Git Bisect (Finding Bugs)

```bash
# Start bisect session
git bisect start

# Mark current commit as bad
git bisect bad

# Mark a known good commit
git bisect good <commit-hash>

# Git will checkout commits for you to test
# Mark each as good or bad
git bisect good  # or git bisect bad

# When done, reset
git bisect reset
```

#### Git Hooks

```bash
# List available hooks
ls .git/hooks/

# Common hooks:
# pre-commit - runs before commit
# post-commit - runs after commit
# pre-push - runs before push
# post-receive - runs after receiving push (server-side)
```

#### Git Worktree (Multiple Working Directories)

```bash
# List worktrees
git worktree list

# Add new worktree
git worktree add <path> <branch-name>

# Remove worktree
git worktree remove <path>
```

### 🔐 Git Security & Best Practices

#### Signing Commits

```bash
# Generate GPG key and configure Git
git config --global user.signingkey <key-id>
git config --global commit.gpgsign true

# Sign a specific commit
git commit -S -m "Signed commit"
```

#### Clean Up Repository

```bash
# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Preview what will be removed
git clean -n

# Garbage collect and optimize repository
git gc --aggressive
```

### 📋 Git Configuration Tips

#### Global Git Configuration

```bash
# Set default editor
git config --global core.editor "code --wait"

# Set default merge tool
git config --global merge.tool vimdiff

# Set default push behavior
git config --global push.default simple

# Enable colored output
git config --global color.ui auto

# Set line ending handling
git config --global core.autocrlf true  # Windows
git config --global core.autocrlf input # Mac/Linux
```

#### Repository-specific Configuration

```bash
# Set config for current repository only
git config user.name "Work Name"
git config user.email "work@company.com"
```

### 📊 Git Statistics & Analysis

#### Repository Statistics

```bash
# Count total commits
git rev-list --all --count

# Show commit count by author
git shortlog -sn

# Show file change statistics
git diff --stat

# Show repository size
git count-objects -vH

# Show most changed files
git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10
```

---

## 💡 Best Practices

1. **Write clear commit messages** - Use present tense and be descriptive
2. **Commit often** - Small, logical commits are easier to manage
3. **Use branches** - Keep main branch stable, develop in feature branches
4. **Pull before push** - Always sync with remote before pushing
5. **Review before commit** - Use `git diff` to check your changes
6. **Use .gitignore** - Exclude files that shouldn't be tracked
7. **Test before pushing** - Ensure code works before sharing
8. **Use meaningful branch names** - feature/user-authentication, bugfix/login-error
9. **Keep commits atomic** - One logical change per commit
10. **Document your workflow** - Team should agree on Git workflow

---

## 🚨 Common Git Problems & Solutions

### Problem: Merge Conflicts
```bash
# When you see conflict markers (<<<<< ===== >>>>>)
# 1. Edit the file to resolve conflicts
# 2. Add the resolved file
git add <conflicted-file>
# 3. Complete the merge
git commit
```

### Problem: Pushed Wrong Commit
```bash
# If you haven't pushed yet
git reset --soft HEAD~1

# If you've already pushed (creates new commit)
git revert <commit-hash>
git push origin <branch-name>
```

### Problem: Need to Change Last Commit Message
```bash
# If not pushed yet
git commit --amend -m "New commit message"

# If already pushed (use with caution)
git commit --amend -m "New commit message"
git push --force-with-lease origin <branch-name>
```

### Problem: Accidentally Deleted Branch
```bash
# Find the commit hash from reflog
git reflog

# Recreate branch from commit
git checkout -b <branch-name> <commit-hash>
```

---

## 🔗 Helpful Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Git Handbook](https://guides.github.com/introduction/git-handbook/)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Pro Git Book](https://git-scm.com/book/en/v2)

---

**Created by:** Mohammed Sufyan  
**Company:** BMW TechWorks India  
**Last Updated:** September 27, 2025