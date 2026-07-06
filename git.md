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
---
---
---
---
# 3 – Git Objects and the Commit Graph

---

# 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Explain what Git Objects are.
- Understand Blob Objects.
- Understand Tree Objects.
- Understand Commit Objects.
- Understand how commits are connected.
- Explain why Git is a Directed Acyclic Graph (DAG).

---

# Introduction

One of the reasons Git is so fast and efficient is its internal object model.

Unlike traditional version control systems, Git does **not** store complete copies of your project for every version. Instead, it stores a collection of objects that together represent your project's history.

Almost everything Git stores internally can be represented using just three object types:

1. Blob
2. Tree
3. Commit

Understanding these objects will make advanced Git topics such as branching, merging, rebasing, and conflict resolution much easier to understand.

---

# Everything in Git is an Object

Git stores information as objects inside the `.git/objects` directory.

The three fundamental object types are:

- Blob
- Tree
- Commit

Everything else in Git is built on top of these objects.

---

# Example Project

Consider the following project:

```text
portfolio/
│
├── README.md
├── app.py
└── src/
    ├── main.py
    └── utils.py
```

Git converts this directory structure into objects.

---

# Blob Object

Blob stands for **Binary Large Object**.

A Blob stores only the **contents of a file**.

Suppose `README.md` contains:

```text
Hello Git
```

Git stores:

```text
Blob
└── "Hello Git"
```

Notice what is **not** stored:

- filename
- directory name
- permissions
- timestamps

A Blob contains **only the file contents**.

---

# Tree Object

A Tree represents a directory.

For our project:

```text
portfolio/
├── README.md
├── app.py
└── src/
```

Git creates a Tree object that contains:

```text
Tree
├── README.md → Blob A
├── app.py    → Blob B
└── src       → Tree C
```

The `src` directory is itself another Tree:

```text
Tree C
├── main.py  → Blob D
└── utils.py → Blob E
```

A Tree acts like a directory map, connecting filenames to Blob or Tree objects.

---

# Commit Object

A Commit represents a snapshot of your project.

A Commit stores:

- A pointer to the root Tree
- Author information
- Commit date
- Commit message
- Parent commit

Example:

```text
Commit
│
├── Tree
├── Author: Utpal
├── Date: 06 July 2026
├── Message: "Initial Commit"
└── Parent: None
```

For later commits:

```text
Commit
│
├── Tree
├── Author
├── Date
├── Message
└── Parent → Previous Commit
```

---

# Relationship Between Objects

Git organizes objects like this:

```text
Commit
   │
   ▼
 Tree
 ├── README.md → Blob
 ├── app.py    → Blob
 └── src
      │
      ▼
     Tree
     ├── main.py  → Blob
     └── utils.py → Blob
```

A Commit points to a Tree.

A Tree points to Blobs and other Trees.

Blobs contain the actual file contents.

---

# What Happens When One File Changes?

Suppose only `README.md` changes.

Git creates:

- One new Blob
- One updated Tree
- One new Commit

Everything else is reused.

Instead of copying thousands of files, Git stores only the new objects required to represent the changes.

This is one reason Git is extremely efficient.

---

# Commit Chain

Suppose we create three commits.

```text
Commit A
    │
    ▼
Commit B
    │
    ▼
Commit C
```

Internally:

```text
Commit C
│
└── Parent → Commit B

Commit B
│
└── Parent → Commit A
```

Each commit stores a reference to its parent.

Together these references create the project's history.

---

# Why Git is Called a DAG

Git's history is a **Directed Acyclic Graph (DAG)**.

Let's understand each word.

## Directed

Each commit points in one direction.

```text
A → B → C
```

---

## Acyclic

The graph never forms a loop.

This is impossible:

```text
A → B → C
↑       │
└───────┘
```

Git history always moves forward.

---

## Graph

A graph is simply a collection of connected nodes.

Git commits form a graph because each commit points to another commit.

---

# Branch Example

Initially:

```text
A → B → C
```

Create a branch:

```text
           C (main)
          /
A → B
          \
           D → E (feature-login)
```

Both branches share the same history until they diverge.

---

# Merge Example

Later:

```text
A → B → C
      \
       D → E
            \
             M
```

`M` is a Merge Commit.

It has **two parents**.

We'll study merge commits in a later lesson.

---

# HEAD Revisited

HEAD points to your current commit.

Example:

```text
HEAD
 │
 ▼
Commit C
```

After another commit:

```text
HEAD
 │
 ▼
Commit D
```

HEAD automatically moves to the newest commit on the current branch.

---

# Why Git is Fast

Git creates only the objects that have changed.

Suppose a React project contains:

```text
3000 files
```

You modify:

```text
App.jsx
```

Git typically creates:

- One Blob
- One Tree
- One Commit

instead of copying all 3000 files.

This object-based design is what makes Git so efficient.

---

# Inspecting Objects

View commit history:

```bash
git log --oneline
```

Inspect the current Commit object:

```bash
git cat-file -p HEAD
```

Example output:

```text
tree 3a0d...
parent e27c...
author Utpal
committer Utpal

Initial Commit
```

View the corresponding Tree:

```bash
git cat-file -p HEAD^{tree}
```

This displays the directory structure stored by Git.

---

# Real-World Example

Suppose your portfolio project contains:

```text
500 files
```

You change only:

```text
Navbar.jsx
```

Git does **not** duplicate all 500 files.

Instead it creates:

- One new Blob
- One updated Tree
- One new Commit

Everything else is reused from previous commits.

---

# Key Takeaways

- Git stores everything as objects.
- Blob objects store file contents.
- Tree objects represent directories.
- Commit objects represent snapshots.
- Commits point to parent commits.
- Git history forms a Directed Acyclic Graph (DAG).
- HEAD points to the current commit.
- Git's object model makes commits extremely fast and storage efficient.

---

# Exercise

Run the following commands inside one of your repositories.

View commit history:

```bash
git log --oneline
```

Inspect the current commit:

```bash
git cat-file -p HEAD
```

Inspect the current tree:

```bash
git cat-file -p HEAD^{tree}
```

Observe:

- Tree
- Parent
- Author
- Commit message

---

# Summary

In this lesson you learned the internal object model used by Git.

Git stores information using three object types:

- Blob
- Tree
- Commit

These objects are connected together to form the commit graph.

Understanding this architecture provides the conceptual foundation for advanced Git topics such as branching, merging, rebasing, and conflict resolution.

---









