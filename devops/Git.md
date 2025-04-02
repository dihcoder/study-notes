# Git

Git is a distributed version control system (DVCS) that allows developers to track changes in files. It is free, open-source, and was developed in 2005 by Linus Torvalds, the creator of the Linux kernel.

## Basic Commands

```sh
# Restore a file to a previous state (discarding/rejecting local changes)
git checkout -- file-name

# Change to a commit or an specific tag (without changing the branch)
git checkout <commit-hash>

# Creating a New Branch
git checkout -b <new-branch-name>

# Deleting a Local Branch (If Merged)
git branch -d <branch-name>

# Forcibly Deleting a Local Branch
git branch -D <branch-name>

# Deleting a Remote Branch
git push origin --delete <branch-name>

# Updating Local References & Removing Deleted Remote Branches
git fetch --prune

# Pulling Remote Changes to Local
git pull origin <branch-name>

# Linking Local to Remote Repository
git remote add origin <repository-url>

# Merging Branches
git merge <branch-name>

# Pushing a New Branch & Opening a Pull Request
git push --set-upstream origin <new-branch-name>
# OR
git push -u origin <new-branch-name>

# Viewing Differences Between Local & Remote
git diff  # Press 'q' to exit

# Amending the Last Commit Message
git commit --amend -m "New comment"

# Viewing Differences in Staged Changes
git diff --staged  # Press 'q' to exit

# Resetting Local Changes to Remote State
git reset --hard origin/master
```

## Advanced Commands

```sh
# Rebasing Local Changes with Remote History
git pull --rebase origin main

# Cherry-picking Commits Between Branches
git cherry-pick <commit-hash>

# Forcing a Push (Overwriting Remote History)
git push origin main --force

# Displaying Repository History in a Graph Format
git log --all --decorate --oneline --graph
```

# GitHub

GitHub is an online platform that hosts Git repositories and enables collaboration among developers. It functions like a social network for programmers, allowing users to:
1. Store and share projects.
2. Improve code through command-line tools, issue tracking, pull requests, and code reviews.
3. Maintain cloud-based projects and track progress.
4. Share knowledge with others.

# GitHub CLI

GitHub CLI is a command-line tool that allows interaction with GitHub directly from the terminal. It provides access to features like pull requests, issues, GitHub Actions, and more.

### Features:
- Manage repositories (view, create, clone, fork).
- Handle issues and pull requests (create, close, edit, list, merge, review, diff).
- Execute and manage GitHub Actions workflows.
- Manage releases and gists.
- Retrieve data from the GitHub API.

### Installation:
```sh
snap info gh

sudo snap install gh

gh help
```

### Basic Commands:

```sh
gh auth login

gh issue list

# Lists all issues with the ‘bug’ label
gh issue list --label "bug"

# Opens your browser to open the issue number 11
gh issue view 11

# Creates an issue from your cli
gh issue create

gh issue status
```

### Working with PR’s (Pull Requests):
```sh
gh pr --help

gh pr list

gh pr list -s "all"

gh pr status

# Checkout into the associated branch for pull request number 9
gh pr checkout 9

gh pr master/main

# Opens your browser to open pr 9
gh pr view 9

# Creates a new pr - but you should create a new branch before and finish your work
gh pr create

# Lists all the merged prs
gh pr list --state "merged"
```

# GitFlow Workflow

GitFlow is a branching model for managing a project's version control. It helps organize the development of new features, bug fixes, and releases efficiently.

## Workflow Structure

![GitFlow Workflow](./imgs/Imagem1.png)
![GitFlow Workflow](./imgs/Imagem2.png)
![GitFlow Workflow](./imgs/Imagem3.png)

- The `develop` branch is the primary branch for development.
- Feature branches are created from `develop` and merged back once completed.
- Releases are created from `develop`, tested, and merged into `main`.
- Hotfixes are created directly from `main` for urgent fixes.
- Changes from `release` and `hotfix` branches must be reflected in `develop`.

### Summary:
1. `develop` is created from `main`.
2. `release` branches are created from `develop`.
3. Feature branches are created from `develop`.
4. Features are merged into `develop`.
5. Releases are merged into both `main` and `develop`.
6. Hotfixes are created from `main`, then merged back into `main` and `develop`.

## Commands:

```sh
# Initialize GitFlow
git flow init

# Start a Feature Branch
git flow feature start <feature-name>

# Finish a Feature Branch
git flow feature finish <feature-name>

# Publish a Feature Branch
git flow feature publish <feature-name>

# Start a Release
git flow release start 1.0

# Finish a Release
git flow release finish 1.0

# Start a Hotfix
git flow hotfix start 1.1

# Finish a Hotfix
git flow hotfix finish 1.1

# Push All Local Branches to GitHub
git push --all
```