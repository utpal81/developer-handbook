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



