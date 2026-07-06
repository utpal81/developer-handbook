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
---
---
---
---
# 4 – Branches: Git's Superpower

---

# 🎯 Learning Objectives

- Explain what a Git branch is.
- Understand why branches are lightweight.
- Explain how Git creates branches instantly.
- Understand the relationship between branches and commits.
- Understand the role of HEAD.
- Create, switch, and delete branches confidently.

---

# Introduction

One of Git's biggest strengths is its branching model.

In many older version control systems, creating a branch meant copying the entire project.

Git does **not** do that.

Instead, a branch is simply a **pointer** to a commit.

This makes branch creation almost instantaneous.

---

# What is a Branch?

Suppose your repository currently looks like this:

```text
A → B → C
```

You are currently working on:

```text
main
```

Internally Git stores:

```text
main
 │
 ▼
 C
```

Notice that **main is only pointing to Commit C**.

The branch itself contains no files.

---

# What Happens When You Commit?

Suppose you make another commit.

Before:

```text
main
 │
 ▼
 C
```

After:

```text
A → B → C → D
              ▲
              │
            main
```

Git simply moves the branch pointer.

Nothing is copied.

---

# Creating a Branch

Create a branch:

```bash
git branch feature-login
```

Git creates another pointer.

```text
A → B → C
          ▲
          │
        main

          ▲
          │
feature-login
```

Both branches point to the same commit.

No files are copied.

---

# Switching Branches

Move to the new branch:

```bash
git switch feature-login
```

(or)

```bash
git checkout feature-login
```

Now:

```text
HEAD
 │
 ▼
feature-login
 │
 ▼
 C
```

HEAD always points to the currently checked-out branch.

---

# Making a Commit

Create another commit.

```text
A → B → C → D
              ▲
              │
      feature-login

main
 │
 ▼
 C
```

Notice:

The **main** branch did not move.

Only **feature-login** moved.

---

# Continue Working

Another commit:

```text
A → B → C → D → E
                  ▲
                  │
          feature-login

main
 │
 ▼
 C
```

The two branches have now diverged.

---

# Switching Back

```bash
git switch main
```

Git moves HEAD.

```text
HEAD
 │
 ▼
main
 │
 ▼
 C
```

Your working directory now reflects Commit C.

It looks as though commits D and E disappeared.

They didn't.

They belong to another branch.

---

# Why This is Amazing

Imagine your project contains:

- 20,000 files
- 5 GB of data

Creating a branch still takes almost no time.

Why?

Because Git only creates another pointer.

It does **not** duplicate your project.

---

# Branches are Cheap

Internally:

```text
main
 │
 ▼
Commit C
```

Feature branch:

```text
feature-login
 │
 ▼
Commit C
```

That's all.

A branch is just a name pointing to a commit.

---

# Viewing Branches

List branches:

```bash
git branch
```

Example:

```text
* main
  feature-login
```

The asterisk indicates the current branch.

---

# Create and Switch

Instead of:

```bash
git branch feature-api

git switch feature-api
```

Use:

```bash
git switch -c feature-api
```

This creates and switches in one command.

---

# Deleting a Branch

After merging:

```bash
git branch -d feature-login
```

Git removes only the pointer.

The commits remain if they are still reachable from another branch.

---

# Real-World Workflow

Imagine you're adding authentication.

Never work directly on:

```text
main
```

Instead:

```bash
git switch -c feature-auth
```

Develop.

Commit.

Test.

Merge back into main.

This keeps the main branch stable.

---

# Professional Branch Naming

Good names:

```text
feature-login

feature-dashboard

bugfix-navbar

hotfix-payment

refactor-auth

docs-readme
```

Avoid:

```text
branch1

test

new

abc
```

Branch names should describe their purpose.

---

# How HEAD Works

Suppose:

```text
main
 │
 ▼
C
```

HEAD contains:

```text
HEAD
 │
 ▼
main
```

Switch branches:

```bash
git switch feature-login
```

HEAD changes:

```text
HEAD
 │
 ▼
feature-login
```

HEAD always follows the active branch.

---

# Visual Summary

```text
                 HEAD
                  │
                  ▼
feature-login → Commit E
                  │
                  ▼
                Commit D
                  │
                  ▼
main ---------> Commit C
                  │
                  ▼
                Commit B
                  │
                  ▼
                Commit A
```

---

# Exercise

Inside a practice repository:

Check the current branch:

```bash
git branch
```

Create a branch:

```bash
git branch feature-test
```

List branches:

```bash
git branch
```

Switch:

```bash
git switch feature-test
```

Verify:

```bash
git branch
```

Switch back:

```bash
git switch main
```

Delete the branch:

```bash
git branch -d feature-test
```

---

# Real Example (Portfolio Website)

Suppose you're adding a new Skills section.

Instead of changing `main`:

```bash
git switch -c feature-skills
```

Work only on that branch.

After testing:

Merge it into:

```text
main
```

This protects your production-ready code.

---

# Common Mistakes

❌ Doing all development on `main`.

❌ Creating meaningless branch names.

❌ Forgetting to switch branches before starting new work.

❌ Deleting a branch before its work has been merged.

---

# Key Takeaways

- A branch is **not** a copy of the project.
- A branch is simply a pointer to a commit.
- Creating a branch is almost instantaneous.
- HEAD points to the currently checked-out branch.
- Commits move the current branch forward.
- Branches allow parallel development safely.

---

# Assignment

Create a practice repository.

Perform the following steps:

1. Create a new repository.
2. Make an initial commit.
3. Create a branch named `feature-demo`.
4. Switch to that branch.
5. Create another commit.
6. Switch back to `main`.
7. Observe that the new commit is no longer visible.
8. Explain why.

---
# Summary

In this lesson you learned that a Git branch is nothing more than a lightweight pointer to a commit.

Because branches are simply pointers, Git can create them instantly regardless of the project size.

This elegant design enables developers to work on multiple features simultaneously while keeping the main branch stable.

---
---
---
---
---
# 5 – Merging Branches

---

# 🎯 Objectives

- Explain why branches are merged.
- Understand Fast-Forward Merge.
- Understand Three-Way Merge.
- Understand Merge Commits.
- Resolve merge conflicts.
- Apply best practices for merging.

---

# Why Do We Merge?

Suppose your repository starts like this:

```text
A → B → C   (main)
```

You create a feature branch:

```bash
git switch -c feature-login
```

Now both branches point to Commit C.

```text
              main
                │
                ▼
A → B → C
          ▲
          │
 feature-login
```

---

# Development Continues

You make two commits.

```text
A → B → C → D → E
                  ▲
                  │
          feature-login

main
 │
 ▼
 C
```

Your feature is complete.

Now you want those commits on `main`.

This is called **merging**.

---

# Merge Command

Switch to the destination branch.

```bash
git switch main
```

Merge:

```bash
git merge feature-login
```

Git now combines the histories.

---

# Fast-Forward Merge

This is the simplest merge.

Before:

```text
main

↓

A → B → C

↓

feature

↓

D → E
```

More clearly:

```text
A → B → C → D → E
                  ▲
                  │
          feature-login

main
 │
 ▼
 C
```

Git notices:

> "main has not changed."

So it simply moves the pointer.

After:

```text
A → B → C → D → E
                  ▲
                  │
         main

                  ▲
                  │
        feature-login
```

No new commit is created.

Git only moves the `main` pointer.

This is called a **Fast-Forward Merge**.

---

# Why "Fast-Forward"?

Git simply fast-forwards the branch pointer.

No history is combined.

Nothing complicated happens.

---

# Three-Way Merge

Now suppose something different happens.

Initial history:

```text
A → B → C
```

Create feature branch.

Then both branches continue independently.

```text
           D → E
          /
A → B → C
          \
           F → G
```

Where

```
D → E
```

belongs to

```
feature-login
```

and

```
F → G
```

belongs to

```
main
```

Now Git cannot simply move a pointer.

It must combine both histories.

---

# Merge Commit

Git creates a special commit.

```text
           D → E
          /      \
A → B → C         M
          \      /
           F → G
```

`M`

is called a **Merge Commit**.

Unlike ordinary commits,

Merge Commit has

**two parents**.

Parent 1:

```
E
```

Parent 2:

```
G
```

---

# Visualizing the Parents

Ordinary commit:

```text
Commit

↓

Parent
```

Merge Commit:

```text
        Merge

      ↙       ↘

 Parent 1   Parent 2
```

This is why Git history becomes a graph.

---

# Merge Conflict

Suppose

Both branches modify

```text
app.py
```

Feature branch:

```python
title = "Login"
```

Main branch:

```python
title = "Authentication"
```

Git doesn't know which version is correct.

Result:

```
Merge Conflict
```

---

# Conflict Markers

Git inserts markers.

```text
<<<<<<< HEAD

title = "Authentication"

=======

title = "Login"

>>>>>>> feature-login
```

Meaning:

Everything between

```text
<<<<<<< HEAD
```

and

```text
=======
```

belongs to

```
main
```

Everything below

```
=======
```

belongs to

```
feature-login
```

---

# Resolving Conflict

Edit manually.

Choose:

```python
title = "User Authentication"
```

Remove the markers.

Save.

Stage:

```bash
git add app.py
```

Finish:

```bash
git commit
```

Merge complete.

---

# Checking History

Use

```bash
git log --oneline --graph
```

Example:

```text
*   Merge feature-login

|\

| * Login page

| *

* | Navbar update

|/

* Initial Commit
```

The graph shows the merge visually.

---

# Fast-Forward vs Three-Way Merge

Fast-Forward

```text
A → B → C → D
```

Only pointer moves.

---

Three-Way

```text
      D → E

     /      \

A → B → C    M

     \      /

      F → G
```

New Merge Commit.

---

# Real Example

Portfolio Website

Branch:

```
feature-skills
```

Another developer works on

```
feature-contact
```

Both branches finish.

Git merges them into

```
main
```

without affecting each other's work.

---

# Best Practices

✔ Keep feature branches small.

✔ Merge frequently.

✔ Pull latest changes before merging.

✔ Write meaningful commit messages.

✔ Delete merged branches.

---

# Commands

Create branch

```bash
git switch -c feature-login
```

Merge

```bash
git switch main

git merge feature-login
```

Delete merged branch

```bash
git branch -d feature-login
```

View graph

```bash
git log --graph --oneline --all
```

---

# Exercise

Create a practice repository.

1.

```bash
git init
```

2.

Create first commit.

3.

Create

```text
feature-demo
```

4.

Make two commits.

5.

Switch back to

```text
main
```

6.

Make another commit.

7.

Merge.

Observe whether Git performs

- Fast-Forward

or

- Three-Way Merge.

---

# Common Mistakes

❌ Editing conflict markers incorrectly.

❌ Forgetting to stage resolved files.

❌ Deleting feature branches before merging.

❌ Working directly on `main`.

---

# Key Takeaways

- Merging combines branch histories.
- Fast-Forward Merge only moves a pointer.
- Three-Way Merge creates a Merge Commit.
- Merge Commits have two parents.
- Merge conflicts occur when Git cannot decide between competing changes.
- Conflicts are resolved manually.

---

# Assignment

Create two branches.

Modify the same file differently.

Merge them.

Observe:

- Conflict markers
- Merge Commit
- Git graph

Explain why the conflict occurred.

---

# Summary

Git merges branches by combining their commit histories.

If one branch is simply ahead of the other, Git performs a **Fast-Forward Merge**.

If both branches have diverged, Git performs a **Three-Way Merge**, creating a special Merge Commit with two parents.

Understanding these merge strategies helps developers collaborate confidently and resolve conflicts when they arise.

---
---
---
---
---

# 6 – Rebasing: Rewriting History

---

# 🎯 Objectives

- Explain what rebasing is.
- Distinguish between Merge and Rebase.
- Understand how Git moves commits during a rebase.
- Use Interactive Rebase.
- Squash multiple commits into one.
- Know when rebasing is appropriate and when it is dangerous.

---

# Why Do We Need Rebase?

Suppose the history starts like this.

```text
A → B → C
```

Create a feature branch.

```text
feature-login
```

Now:

```text
A → B → C
          ▲
          │
        main
          ▲
          │
 feature-login
```

---

# Development Continues

Feature branch:

```text
A → B → C → D → E
```

Meanwhile, another developer updates main.

```text
A → B → C → F → G
```

Now the histories have diverged.

---

# Option 1 – Merge

Using

```bash
git merge feature-login
```

produces

```text
          D → E
         /      \
A → B → C        M
         \      /
          F → G
```

History is preserved exactly as it happened.

A Merge Commit is created.

---

# Option 2 – Rebase

Instead:

```bash
git switch feature-login

git rebase main
```

Git says:

> "Pretend you started working after Commit G."

Git temporarily removes:

```
D

E
```

Moves to:

```
G
```

Then reapplies

```
D

E
```

One by one.

Result:

```text
A → B → C → F → G → D' → E'
```

Notice:

They are

```
D'

E'
```

Not

```
D

E
```

Git created **new commits**.

---

# Why New Commits?

Commits are immutable.

Once created,

they never change.

Therefore,

Git creates

```
D'

E'
```

instead of modifying

```
D

E
```

---

# Merge vs Rebase

Merge

```text
          D → E
         /      \
A → B → C        M
         \      /
          F → G
```

History preserved.

---

Rebase

```text
A → B → C → F → G → D' → E'
```

Linear history.

No Merge Commit.

---

# Advantages of Rebase

✔ Cleaner history

✔ Easier to read

✔ No unnecessary Merge Commits

✔ Better for feature branches

---

# Disadvantages

History changes.

Commit IDs change.

Previously shared commits disappear.

This is why rebasing shared branches can be dangerous.

---

# Interactive Rebase

One of Git's most powerful tools.

Run

```bash
git rebase -i HEAD~3
```

Git opens

```text
pick a1b2 First commit

pick c3d4 Second commit

pick e5f6 Third commit
```

---

# Squashing Commits

Suppose your history is

```text
Add login page

Fix typo

Fix CSS

Fix button

Fix typo again
```

This is messy.

Interactive rebase allows

```text
pick Add login page

squash Fix typo

squash Fix CSS

squash Fix button

squash Fix typo again
```

Result

```text
Add complete login feature
```

One clean commit.

---

# Reordering Commits

Interactive rebase also lets you reorder commits.

Before

```text
A

B

C
```

After

```text
A

C

B
```

---

# Editing Commit Messages

Suppose

```text
git commit

"asdf"
```

Oops.

Use

```bash
git rebase -i HEAD~1
```

Choose

```text
reword
```

Git lets you write a proper message.

---

# Removing Commits

Interactive rebase

Delete

```text
pick
```

line

or choose

```text
drop
```

Commit disappears.

---

# Visual Example

Before

```text
main

↓

A → B → C

↓

feature

↓

D → E
```

Meanwhile

```text
main

↓

A → B → C → F → G
```

After rebase

```text
A → B → C → F → G → D' → E'
```

---

# Real Example

Portfolio Website

You make

```text
20 tiny commits
```

```
Fix typo

Spacing

Button

Color

Navbar

Footer

Image
```

Before opening a Pull Request

Use

```bash
git rebase -i
```

Squash everything into

```text
Complete Portfolio Homepage
```

Much cleaner.

---

# When Should You Use Rebase?

Good

✔ Before opening Pull Request

✔ Cleaning your own commits

✔ Keeping feature branches updated

✔ Local branches

---

# When Should You NOT Use Rebase?

Never rebase

- main

- shared branches

- commits already pushed that others may have based work on

Otherwise,

everyone else's history breaks.

---

# Golden Rule

> Rebase your own work.

Never rewrite someone else's history.

---

# Useful Commands

Rebase current branch

```bash
git rebase main
```

Interactive rebase

```bash
git rebase -i HEAD~5
```

Abort

```bash
git rebase --abort
```

Continue

```bash
git rebase --continue
```

---

# Rebase Conflict

Sometimes

Git stops.

Example

```text
CONFLICT

app.py
```

Fix

```text
app.py
```

Then

```bash
git add app.py

git rebase --continue
```

Repeat until complete.

---

# Merge or Rebase?

Use Merge when

- preserving exact history matters

- working on shared branches

Use Rebase when

- cleaning local history

- preparing Pull Requests

- updating feature branches

---

# Common Mistakes

❌ Rebasing main

❌ Rebasing commits already pushed publicly

❌ Forgetting to resolve conflicts

❌ Force pushing without understanding the consequences

---

# Hands-on Exercise

Create a repository.

Create

```
feature-demo
```

Make

```
5 commits
```

Use

```bash
git rebase -i HEAD~5
```

Squash them into

```
One clean commit
```

Observe

```bash
git log --oneline
```

---

# Key Takeaways

- Merge preserves history.
- Rebase rewrites history.
- Rebase creates new commits.
- Interactive Rebase cleans commit history.
- Squashing makes history easier to read.
- Never rewrite shared history.

---

# Summary

Rebasing is Git's mechanism for moving a sequence of commits onto a new base commit.

Unlike merging, which combines histories using a Merge Commit, rebasing rewrites history by creating new commits.

Interactive Rebase provides powerful tools for cleaning, squashing, reordering, and editing commits before sharing your work.

Understanding when to merge and when to rebase is one of the most important skills in professional Git workflows.

---



# 7 – Undoing Mistakes in Git

---

# 🎯 Objectives

- Understand the different ways of undoing changes.
- Know when to use:
  - `git restore`
  - `git reset`
  - `git revert`
  - `git checkout`
  - `git reflog`
- Recover deleted commits.
- Recover deleted branches.
- Avoid common mistakes when undoing work.

---

# Introduction

One of Git's greatest strengths is that almost nothing is permanently lost immediately.

Most mistakes can be recovered.

However, different mistakes require different commands.

This lesson helps you answer one question:

> "Which Git command should I use?"

---

# The Four Places Where Changes Can Exist

Before learning the commands, remember Git's workflow.

```text
Working Directory
        │
        ▼
Staging Area
        │
        ▼
Repository
        │
        ▼
Remote Repository
```

Every undo command affects one or more of these areas.

---

# Situation 1

## You modified a file but haven't staged it.

Example

```bash
git status
```

Output

```text
modified: app.py
```

You decide:

> "I don't want these changes."

Use

```bash
git restore app.py
```

Result

```text
Working Directory

↓

Previous committed version
```

Only the working directory changes.

Nothing else changes.

---

# Situation 2

## You staged the wrong file.

```bash
git add app.py
```

Oops.

You don't want it staged.

Use

```bash
git restore --staged app.py
```

Result

```text
Working Directory
    ✓

Staging Area
    Removed
```

The file remains edited.

It simply leaves the staging area.

---

# Situation 3

## You made a commit.

```bash
git commit -m "Wrong commit"
```

Now you want to remove it.

Use

```bash
git reset
```

But there are three kinds.

---

# Soft Reset

```bash
git reset --soft HEAD~1
```

Result

```text
Commit removed

↓

Changes remain staged
```

Visual

```text
Before

Working
↓

Stage
↓

Commit A
↓

Commit B
```

After

```text
Working
↓

Stage
↓

Commit A
```

Files are still staged.

---

# Mixed Reset (Default)

```bash
git reset HEAD~1
```

or

```bash
git reset --mixed HEAD~1
```

Result

```text
Commit removed

↓

Changes remain

↓

Not staged
```

This is the default behavior.

---

# Hard Reset

```bash
git reset --hard HEAD~1
```

Result

```text
Commit removed

↓

Working Directory removed

↓

Stage removed
```

Everything goes back.

Use with extreme caution.

---

# Visual Comparison

## Soft

```text
Commit ❌

Stage ✓

Working ✓
```

---

## Mixed

```text
Commit ❌

Stage ❌

Working ✓
```

---

## Hard

```text
Commit ❌

Stage ❌

Working ❌
```

---

# Situation 4

## You already pushed the commit.

Never use

```bash
git reset
```

Instead

```bash
git revert
```

---

# What Does Revert Do?

Suppose

```text
A → B → C
```

Commit

```
C
```

introduced a bug.

Run

```bash
git revert C
```

Git creates

```text
A → B → C → D
```

Where

```
D
```

undoes

```
C
```

Notice

History is preserved.

Nothing disappears.

This is why teams prefer

```bash
git revert
```

on shared branches.

---

# Situation 5

## Detached HEAD

Suppose

```bash
git checkout 4d5ab2
```

Git says

```text
Detached HEAD
```

Meaning

HEAD points directly to a commit.

Not to a branch.

You're no longer on

```text
main
```

or

```text
feature
```

You're simply looking at an old snapshot.

Return

```bash
git switch main
```

---

# Situation 6

## You accidentally deleted a branch.

Example

```bash
git branch -D feature-login
```

Oops.

Can Git recover it?

Usually yes.

Use

```bash
git reflog
```

---

# What is Reflog?

Git records every movement of HEAD.

Example

```text
HEAD@{0}

HEAD@{1}

HEAD@{2}
```

Even deleted commits often appear.

---

# Recover Lost Commit

Suppose

```text
HEAD@{3}

↓

a4b6d9
```

Recover

```bash
git checkout a4b6d9
```

or

```bash
git branch recovered a4b6d9
```

Nothing is lost.

---

# Recover After Hard Reset

Even

```bash
git reset --hard
```

often isn't permanent.

Use

```bash
git reflog
```

Find

```text
HEAD@{5}
```

Recover

```bash
git reset --hard HEAD@{5}
```

Magic!

---

# Real Example

You accidentally delete

```text
Navbar.jsx
```

Run

```bash
git restore Navbar.jsx
```

Recovered instantly.

---

Another example.

You accidentally commit

```text
.env
```

Undo

```bash
git reset --soft HEAD~1
```

Remove

```
.env
```

Commit again.

---

# Which Command Should I Use?

| Situation | Command |
|-----------|----------|
| Discard file changes | `git restore` |
| Unstage a file | `git restore --staged` |
| Undo last commit (keep staged) | `git reset --soft` |
| Undo last commit (keep files) | `git reset` |
| Undo last commit completely | `git reset --hard` |
| Undo pushed commit | `git revert` |
| Recover lost work | `git reflog` |

---

# Common Mistakes

❌ Using `git reset --hard` without understanding it.

❌ Using `git reset` after pushing.

❌ Ignoring `git reflog`.

❌ Panicking before checking the reflog.

---

# Exercise

Create a repository.

1.

Create

```text
hello.txt
```

Commit.

2.

Modify it.

Run

```bash
git restore hello.txt
```

3.

Commit again.

Run

```bash
git reset --soft HEAD~1
```

Observe.

4.

Run

```bash
git reset HEAD~1
```

Observe.

5.

Run

```bash
git reflog
```

Observe the history.

---

# Key Takeaways

- `git restore` affects the working directory.
- `git restore --staged` removes files from staging.
- `git reset` rewrites local history.
- `git revert` creates a new commit that undoes a previous one.
- `git reflog` is one of Git's most valuable recovery tools.
- Most Git mistakes can be recovered if you act before Git's garbage collection removes unreachable objects.

---

# Summary

Git provides several commands for undoing mistakes, each designed for a specific stage of the workflow.

Choosing the correct command depends on whether your changes are:

- Unstaged
- Staged
- Committed
- Already pushed

Understanding these differences helps you recover safely without accidentally losing work.

---















