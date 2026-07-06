# Professional Git

## 1: What is Git Really?

---

## 🎯 Learning Objectives

By the end of this section, I will be able to:

- Explain why Git was created.
- Understand repositories and commits.
- Explain snapshots.
- Understand the three Git areas.
- Distinguish between local and remote repositories.

---

# Why Was Git Created?

Imagine writing a research paper.

Without Git, your folders might look like this:

```text
paper.docx
paper_final.docx
paper_final2.docx
paper_final_revised.docx
paper_final_latest.docx
```

This quickly becomes confusing.

Software projects are much larger.

A project may contain thousands of files.

Copying the entire project every time you make a change wastes both storage and time.

Git solves this problem.

---

# Git's Main Idea

Git stores **snapshots** instead of duplicate folders.

Example:

```text
Commit A
│
├── app.py
└── README.md

↓

Commit B
│
├── app.py (modified)
└── README.md

↓

Commit C
│
├── app.py
├── README.md
└── requirements.txt
```

Each commit represents the complete state of the project at that point in time.

---

# What is a Repository?

A **repository (repo)** is simply a project that Git tracks.

Example:

```text
researchmind-ai/
│
├── app.py
├── README.md
└── .git/
```

The hidden **.git** folder contains:

- Commit history
- Branches
- Tags
- Configuration
- Git objects
- References

Without the **.git** folder, the directory is just an ordinary folder.

---

# What is a Commit?

A commit is **not just saving your work**.

A commit contains:

- Snapshot of the project
- Author
- Date
- Commit message
- Parent commit

Example

```text
Author : Utpal

Date : July 6, 2026

Message :
"Add FastAPI authentication"
```

Think of a commit as a checkpoint in the project's history.

---

# The Three Git Areas

This is the single most important concept in Git.

```text
Working Directory
        │
   git add
        ▼
Staging Area
        │
 git commit
        ▼
Git Repository
```

---

## 1. Working Directory

This is your project folder.

Example:

```text
researchmind-ai/
```

When you edit a file using VS Code, the changes exist only in the working directory.

Git has **not** recorded them yet.

---

## 2. Staging Area

The staging area acts like a preparation area.

Example:

```bash
git add app.py
```

Git understands:

> "Include this version of app.py in the next commit."

The changes are **staged**, but not yet permanently recorded.

---

## 3. Repository

Now create a commit.

```bash
git commit -m "Update login API"
```

Git records the snapshot permanently.

---

# Why Separate `git add` and `git commit`?

Suppose you modified three files:

```text
app.py
README.md
config.py
```

Only **app.py** is ready.

You can stage only that file:

```bash
git add app.py
```

Then commit:

```bash
git commit -m "Fix login bug"
```

The other two files remain uncommitted.

This flexibility is one of Git's greatest strengths.

---

# Local Repository vs Remote Repository

Your computer contains:

```text
researchmind-ai/
└── .git/
```

This is your **Local Repository**.

GitHub contains:

```text
github.com/username/researchmind-ai
```

This is your **Remote Repository**.

Use:

```bash
git push
```

to upload commits.

Use:

```bash
git pull
```

to download commits.

---

# Git vs Cloud Storage

Google Drive stores files.

Git stores:

- History
- Authors
- Branches
- Commits
- Merge information

Git is designed specifically for software development.

---

# Common Git Commands

Check repository status:

```bash
git status
```

Stage changes:

```bash
git add .
```

Commit changes:

```bash
git commit -m "Meaningful commit message"
```

View history:

```bash
git log --oneline
```

---

# Exercise

Use any existing Git project.

Run:

```bash
git status
```

Observe modified files.

Stage all changes:

```bash
git add .
```

Run:

```bash
git status
```

Observe the difference.

Create a commit:

```bash
git commit -m "Practice commit"
```

View history:

```bash
git log --oneline
```

---

# Summary

In this lesson you learned:

- Git stores snapshots, not duplicate folders.
- A repository is a project tracked by Git.
- A commit is a snapshot plus metadata.
- Git uses three areas:
  - Working Directory
  - Staging Area
  - Repository
- Local and remote repositories are different.
- `git add` prepares changes.
- `git commit` permanently records them.

---
---
---
---
---


# 2 – Inside the `.git` Directory

---

# 🎯 Learning Objectives

By the end of this section, I will be able to:

- Explain the purpose of the `.git` directory.
- Understand what Git stores internally.
- Understand `HEAD`.
- Understand branches and references.
- Explain Git objects.
- Explore your own repository confidently.

---

# What is the `.git` Directory?

When you initialize a repository:

```bash
git init
```

Git creates a hidden folder named

```text
.git
```

This folder is the **heart of Git**.

Everything Git knows about your project is stored here.

Without it, your project is just a normal folder.

---

# View the Hidden Directory

Normally:

```bash
ls
```

doesn't show hidden files.

Instead:

```bash
ls -la
```

Example:

```text
.
..
.git
README.md
app.py
```

---

# Explore the `.git` Folder

Move inside:

```bash
cd .git
```

List its contents:

```bash
ls
```

You might see:

```text
HEAD
config
description
hooks
index
objects
refs
logs
info
```

Don't worry—we'll understand each one.

---

# Overview

```text
.git/

├── HEAD
├── config
├── description
├── hooks/
├── index
├── info/
├── logs/
├── objects/
└── refs/
```

---

# 1. HEAD

This is probably the most important file in Git.

Open it:

```bash
cat HEAD
```

Example:

```text
ref: refs/heads/main
```

Meaning:

> "You are currently on the main branch."

HEAD simply tells Git:

**Which branch am I currently working on?**

Think of HEAD as:

```text
Current Position
```

Whenever you switch branches:

```bash
git switch feature-login
```

HEAD changes.

---

# 2. config

Open:

```bash
cat config
```

Example:

```text
[core]
repositoryformatversion = 0
filemode = true
bare = false
```

This stores repository-specific settings.

Examples:

- default branch
- remotes
- merge settings

---

# 3. objects/

This is where Git stores your data.

Everything eventually becomes an object.

Examples:

- commits
- files
- directories

Git stores them here.

This is one reason Git is so efficient.

---

# 4. refs/

References are pointers.

Example:

```text
refs/

    heads/

        main

        feature-login

    tags/
```

Every branch is just a pointer.

The branch itself does **not** contain the files.

It points to the latest commit.

---

# 5. logs/

Git records history here.

When HEAD changes,

Git logs it.

Useful for recovery.

Example:

```bash
git reflog
```

Later we'll use this to recover "lost" commits.

---

# 6. hooks/

Hooks allow Git to execute scripts automatically.

Examples:

Before a commit:

```text
Run tests
```

Before pushing:

```text
Run linter
```

Companies often use hooks to enforce coding standards.

---

# 7. index

The index is the **staging area**.

Remember:

```text
Working Directory

↓

Staging Area

↓

Repository
```

The staging area is stored in

```text
.git/index
```

When you run:

```bash
git add app.py
```

Git updates the index.

When you commit,

Git creates a snapshot from the index.

---

# Visual Picture

```text
VS Code

↓

Working Directory

↓

.git/index

↓

Commit

↓

objects/
```

This explains why

```bash
git add
```

and

```bash
git commit
```

are different operations.

---

# Experiment

Inside one of your repositories:

```bash
ls -la
```

Notice:

```text
.git
```

Go inside:

```bash
cd .git
```

Now run:

```bash
ls
```

Explore:

```bash
cat HEAD
```

```bash
cat config
```

Return:

```bash
cd ..
```

---

# What Happens During a Commit?

Suppose you change:

```text
app.py
```

Then:

```bash
git add app.py
```

Git updates:

```text
index
```

Then:

```bash
git commit
```

Git creates:

- Blob object
- Tree object
- Commit object

Stores them inside:

```text
objects/
```

Updates:

```text
refs/heads/main
```

Moves:

```text
HEAD
```

to the new commit.

---

# Real-World Example

Suppose your repository becomes corrupted.

Knowing that Git's history lives inside

```text
.git/
```

explains why deleting the `.git` directory removes **all commit history**, even though your source files remain.

---

# Commands to Practice

```bash
ls -la

cd .git

ls

cat HEAD

cat config

cd ..
```

---

# Summary

You learned:

- `.git` is the Git database.
- `HEAD` tells Git which branch you're on.
- `index` is the staging area.
- `objects/` stores commits and file contents.
- `refs/` stores branch pointers.
- `logs/` records reference changes.
- `hooks/` stores automation scripts.

---

# Assignment

Using one of your Git projects:

1. Locate the `.git` directory.
2. View the contents with `ls`.
3. Open `HEAD`.
4. Open `config`.
5. Explain in your own words:
   - What is `HEAD`?
   - What is `index`?
   - What is `objects/`?
   - What is `refs/`?

---




