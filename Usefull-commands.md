# Git Cheat Sheet (Beginner → Advanced)

> This cheat sheet contains the most commonly used Git commands.
> Commands that perform the same function are grouped together.
> Examples are included wherever necessary.

---

# 1. Configure Git (One Time Setup)

## Check Git version

```bash
git --version
```

Example:

```text
git version 2.50.1
```

---

## Set your username

```bash
git config --global user.name "Your Name"
```

Example

```bash
git config --global user.name "John Doe"
```

---

## Set your email

```bash
git config --global user.email "you@example.com"
```

Example

```bash
git config --global user.email "john@gmail.com"
```

---

## Check configured username/email

```bash
git config --global --list
```

or

```bash
git config --list
```

---

# 2. Initialize Repository

## Create a Git repository

```bash
git init
```

Example

```bash
cd MyProject
git init
```

Creates a hidden `.git` folder that tracks your project.

---

# 3. Clone Existing Repository

```bash
git clone <repository-url>
```

Example

```bash
git clone https://github.com/user/project.git
```

Clone into a different folder

```bash
git clone https://github.com/user/project.git MyFolder
```

---

# 4. Check Repository Status

```bash
git status
```

Shows

- Modified files
- Staged files
- Untracked files
- Current branch

---

# 5. Staging Files

## Stage one file

```bash
git add file.txt
```

---

## Stage multiple files

```bash
git add file1.txt file2.txt
```

---

## Stage an entire folder

```bash
git add folder/
```

---

## Stage everything

```bash
git add .
```

Stages all changes inside the current directory.

---

```bash
git add -A
```

Stages everything in the repository.

Usually behaves the same as:

```bash
git add .
```

---

## Interactive staging

```bash
git add -p
```

Lets you stage only parts of a file.

---

# 6. Remove Files From Staging

Unstage a file

```bash
git restore --staged file.txt
```

Older equivalent

```bash
git reset HEAD file.txt
```

Both perform the same task.

---

# 7. Commit Changes

Commit

```bash
git commit -m "Your message"
```

Example

```bash
git commit -m "Added login page"
```

---

Stage and commit tracked files

```bash
git commit -am "Updated navbar"
```

Equivalent to

```bash
git add .
git commit -m "Updated navbar"
```

Only works for tracked files.

---

# 8. Commit History

Compact history

```bash
git log --oneline
```

---

Detailed history

```bash
git log
```

---

Graph view

```bash
git log --graph --oneline --all
```

---

# 9. Branches

List branches

```bash
git branch
```

---

List remote branches

```bash
git branch -r
```

---

List all branches

```bash
git branch -a
```

---

Create branch

```bash
git branch feature
```

---

Create and switch

```bash
git switch -c feature
```

Older equivalent

```bash
git checkout -b feature
```

Both do exactly the same thing.

---

Switch branch

```bash
git switch main
```

Older equivalent

```bash
git checkout main
```

Both do the same job.

---

Rename branch

```bash
git branch -m new-name
```

---

Delete branch

```bash
git branch -d feature
```

Deletes merged branch.

---

Force delete

```bash
git branch -D feature
```

Deletes regardless of merge status.

---

# 10. Merge

Merge another branch into current branch

```bash
git merge feature
```

Example

```bash
git switch main
git merge feature
```

---

Abort merge

```bash
git merge --abort
```

---

# 11. Remote Repositories

View remotes

```bash
git remote -v
```

---

Add remote

```bash
git remote add origin https://github.com/user/project.git
```

---

Change remote URL

```bash
git remote set-url origin NEW_URL
```

---

Remove remote

```bash
git remote remove origin
```

---

# 12. Push

First push

```bash
git push -u origin main
```

Equivalent

```bash
git push --set-upstream origin main
```

Both perform the same task.

---

Later pushes

```bash
git push
```

---

Push specific branch

```bash
git push origin feature
```

---

Force push

```bash
git push --force
```

Safer version

```bash
git push --force-with-lease
```

Recommended instead of `--force`.

---

Delete remote branch

```bash
git push origin --delete feature
```

---

# 13. Pull

Download and merge

```bash
git pull
```

---

Specific branch

```bash
git pull origin main
```

---

Download only

```bash
git fetch
```

Difference

```
git fetch
↓
Downloads changes only

git pull
↓
Downloads + merges
```

---

# 14. Restore Changes

Discard changes in one file

```bash
git restore file.txt
```

Older equivalent

```bash
git checkout -- file.txt
```

Both do the same thing.

---

Restore entire project

```bash
git restore .
```

---

# 15. Remove Files

Remove tracked file

```bash
git rm file.txt
```

---

Remove folder

```bash
git rm -r folder
```

---

Keep local file but stop tracking

```bash
git rm --cached file.txt
```

Useful for `.gitignore`.

---

# 16. .gitignore

Ignore files

Example

```text
node_modules/
.env
*.log
dist/
```

---

# 17. Stash

Temporarily save changes

```bash
git stash
```

---

View stashes

```bash
git stash list
```

---

Restore stash

```bash
git stash pop
```

---

Restore without deleting stash

```bash
git stash apply
```

---

Delete stash

```bash
git stash drop
```

---

# 18. Undo Commits

Undo last commit (keep files)

```bash
git reset --soft HEAD~1
```

---

Undo last commit (keep changes unstaged)

```bash
git reset HEAD~1
```

---

Delete commit and changes

```bash
git reset --hard HEAD~1
```

---

# 19. View Differences

Unstaged changes

```bash
git diff
```

---

Staged changes

```bash
git diff --staged
```

---

Between commits

```bash
git diff COMMIT1 COMMIT2
```

---

# 20. Tags

Create tag

```bash
git tag v1.0
```

---

List tags

```bash
git tag
```

---

Push tags

```bash
git push origin --tags
```

---

# 21. Repository Information

Current branch

```bash
git branch
```

or

```bash
git status
```

---

View tracked files

```bash
git ls-files
```

---

Show commit

```bash
git show
```

---

# 22. Helpful Commands

Show Git help

```bash
git help
```

---

Help for a command

```bash
git help commit
```

or

```bash
git commit --help
```

---

# Typical Workflow

```bash
git init

git status

git add .

git commit -m "Initial commit"

git remote add origin https://github.com/username/repository.git

git branch -M main

git push -u origin main
```

---

# Daily Workflow

```bash
git status

git pull

git add .

git commit -m "Describe your changes"

git push
```

---

# Branch Workflow

```bash
git switch -c feature

git add .

git commit -m "Implemented feature"

git push -u origin feature

git switch main

git pull

git merge feature

git push

git branch -d feature

git push origin --delete feature
```

---

# Commands That Do the Same Thing

| Modern | Older | Purpose |
|---------|--------|---------|
| `git switch main` | `git checkout main` | Switch branches |
| `git switch -c feature` | `git checkout -b feature` | Create + switch branch |
| `git restore file.txt` | `git checkout -- file.txt` | Restore file |
| `git restore --staged file.txt` | `git reset HEAD file.txt` | Unstage file |
| `git push -u origin main` | `git push --set-upstream origin main` | Set upstream |
| `git add .` | `git add -A` | Stage almost everything (similar in most cases) |

---

# Git Basics You Should Memorize

```bash
git init
git clone URL
git status
git add .
git commit -m "message"
git log --oneline
git branch
git switch branch
git switch -c branch
git merge branch
git pull
git push
git fetch
git remote -v
git stash
git diff
git restore .
git rm
git tag
```