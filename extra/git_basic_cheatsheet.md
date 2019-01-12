# Git Basics Cheat Sheet
## The Core Concept - Mental Model

Git is a distributed version control system designed to track changes in files over time.

Git works like a mini workflow system. Every file moves through 3 main states:

| State              | Description                                   | How to Work With It     |
|--------------------|-----------------------------------------------|--------------------------|
|  Working Directory | Your actual project folder (where you edit)    | Edit files directly      |
| Staging Area or Index     | Temporary area to prepare commits             | `git add <file>`         |
|  Local Repository | Database of committed snapshots on your machine | `git commit -m "message"` |


### Additional Areas: Remote Repo & Stash
| **Area** | **Description** | **How to Work With It** |
| --- | ---------- | ---------- |
| Remote Repository | Copy of your repository hosted on a server (GitHub, GitLab, etc.) | `git remote -v` (View remote repo),<br> `git push`(upload local commits to remote),<br> `git pull`(download & merge changes from remote),<br> `git fetch` (Only download remote changes (no merge)) |
| Stash | Temporary storage for changes you're not ready to commit (use to switch branches or pull but don't want to lose changes)| `git stash`(Save uncommitted changes temporarily),<br> `git stash pop`(Applies and removes the last stashed changes),<br> `git stash list` (Show all stashed changes) |
|  |  |  |

*It is done this way*

[Working Dir] → `git add` → [Staging Area] → `git commit` → [Local Repo] →` git push` → [Remote Repo]

---------

| Term         | Description                                  | Why It Matters for You                                   |
|--------------|----------------------------------------------|-----------------------------------------------------------|
| **Commit**   | A snapshot of your project at a point in time | Saves your work (code + message). Helps track progress and undo mistakes. |
|              | Each commit has:                              | - Unique ID (SHA), Author info, Commit message, Timestamp, Parent(s) |
| **HEAD**     | Git's "you are here" marker                  | Tells Git what your current working location is — usually the **latest commit** on your current branch. |
|              | Can point to:                                | → A branch (normal)<br>→ A commit (detached HEAD mode) |
| **Branch**   | A movable named pointer to a commit                | Lets you work on new features, experiments, or fixes without affecting the main branch. |
| | Common operations for branch management | `git branch` # Lists all branches<br> `git branch <new-branch>` # Creates a new branch called 'new-branch' <br> `git checkout <branch-name>` # Moves you to the specified branch <br> `git checkout -b <new-branch-name>` # creates a new branch and checks it out immediately.|

| Term     | Meaning                                                                     |
| -------- | --------------------------------------------------------------------------- |
| `origin` | The default name Git gives to the remote repository (e.g., on GitHub).      |
| `main` /`master`  | main is default **primary branch** name for most new repos (modern Git/GitHub) while master in old |


## Undoing Changes and Mistakes

You will make mistakes, and Git has your back:

| Command        | Moves HEAD | Staging Area (Index)| Working Directory         | Typical Use Case                                                |
|----------------|------------|--------------------------|---------------------------|-----------------------------------------------------------------|
| `git restore <file>`| ✗        | ✗ (no effect)            | ✗ (reverts file)         | Discard changes in a file (not staged yet)                      |
| `git restore --staged <file>` | ✗        | ✓ (unstages file)        | ✗ (keeps changes)        | Unstage a file without deleting your changes                    |
| `git reset --soft HEAD~1`     | ✓        | ✓ (keeps changes staged) | ✓ (keeps changes)        | Undo commit, keep staged for recommit (e.g., fix message)       |
| `git reset [--mixed] HEAD~1`  | ✓        | ✗ (unstages)             | ✓ (keeps changes)        | Undo commit and unstage changes to edit or fix before commit    |
| `git reset --hard HEAD~1`     | ✓        | ✗ (clears staging)       | ✗ (discards changes)     | Completely remove last commit and all changes — use with care!  |

## Repository Structure

| **Area** | **Description** |
| --- | --- |
| .git/ | The hidden folder that stores everything Git tracks |
| .gitignore | Tells Git which files/folders to ignore |
| .gitconfig | Global or local Git settings |

## Common Configurations
To set your identity for commit(once per machine)
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

```

And where configs live:

- Global: ~/.gitconfig
- Repo-specific: .git/config

### Add .gitignore

To avoid tracking temporary files like node_modules and sensitive files like .env, add a `.gitignore` file in your repo.

---------------------
# Practical Git WorkFlow
This has step-by-step guide to getting started with Git — from initializing your first repository to collaborating with others.

## Recommended before you start
### Check if Git is Installed
- Open a terminal and run: `git --version`  
If you see something like git version 2.x.x, you're good to go.  
If you get `"command not found"`, Download Git and install it first.  
https://git-scm.com/download/win

### Check your config list
- Use `git config --list` to see the exisitng config list. sample below
```
user.name=<git_user_name>
user.email=<git_user_email>
core.repositoryformatversion=0
```

### Set Your Identity (Recommended for commits)
```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
## Initializing your own Repository
```
### Setup SSH for GitHub (if not already configured)
To avoid password prompts every time you git push or pull, make sure SSH is set up.
- Use `ssh -T git@github.com` to see if connection is set up.   
result: 
`Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.`
- if error  like Permission Denied or Could not resolve hostname, go to   
[ssh_basic_cheatsheet](ssh_basic_cheatsheet.md)

## After set up

### Start a Git Project

- `git init` — Start tracking changes in a new local folder.  
- `git clone <url>` — Copy or download an existing Git repo from GitHub (or similar).
---
### Check What’s Going On

- `git status` — See what's changed, staged, or untracked.  
- `git diff` — View the actual line-by-line differences in your files.
---
### Branching for separating concern, organizing features or testing:

- `git branch` — List all branches  
- `git branch <new-branch>` — Create a new branch  
- `git checkout <branch-name>` — Switch to an existing branch  
- `git checkout -b <new-branch-name>` — Create and switch to a new branch in one step

### Stage Your Changes

- `git add <file>` — Stage a specific file for commit.  
- `git add .` — Stage all changes (use with care).
---
### Commit Your Work

- `git commit -m "Your message"` — Create a commit (a snapshot of your changes).
---
### Push to a Remote

- `git remote -v` — See the remote URL (where `push` sends your commits)
- `git push` — Send your commits to the remote repo (GitHub, GitLab, etc.).
---
### Pull Changes from Remote

- `git pull` — Fetch + merge changes from the remote into your local branch.  
- `git fetch` — Only download (don’t merge yet).
---

### Viewing commit History

- `git log`  View commit history.
- `git log --oneline` — Compact one-liner view  
---

## Quick Tips

- Write clear, meaningful commit messages.  
- Stage only what you want to commit.  
- Use branches to manage different features or fixes.
---

*This cheat sheet covers the basic Git commands to help you get started with version control.*