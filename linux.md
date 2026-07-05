# Linux Developer Handbook

> My personal Linux notes and command reference for becoming a Full-Stack AI Developer.

---

# Table of Contents

1. Linux Filesystem
2. Navigation
3. Files & Directories
4. Viewing Files
5. Searching
6. Permissions
7. Processes
8. Environment Variables
9. Package Management
10. Networking
11. Bash Scripting
12. WSL
13. Useful Tips

---

# 1 - Linux Filesystem & Navigation

## Learning Objectives

After completing this lesson, I should be able to:

- Explain the Linux filesystem hierarchy.
- Navigate directories using the terminal.
- Understand the difference between absolute and relative paths.
- Use `pwd`, `ls`, and `cd` confidently.
- Understand the meaning of `/`, `~`, `.`, and `..`.

---

# 1. Linux Filesystem

Unlike Windows, Linux uses a **single hierarchical filesystem**.

Everything begins from the **root directory**.

```text
                 /
                 │
      ┌──────────┼──────────┐
      │          │          │
     bin       home       etc
                 │
               toutp
                 │
             projects
                 │
        researchmind-ai
```

There are **no C:, D:, or E: drives** in Linux.

Everything belongs to one filesystem.

---

## Windows vs Linux

### Windows

```text
C:\Users\toutp\Projects
D:\Movies
E:\Games
```

### Linux

```text
/home/toutp/projects
/home/toutp/Documents
/usr/bin
```

---

# 2. Important Directories

| Directory | Purpose |
|------------|---------|
| `/` | Root directory |
| `/home` | User home directories |
| `~` | Current user's home directory |
| `/bin` | Essential commands |
| `/usr` | Installed software and libraries |
| `/etc` | System configuration files |
| `/tmp` | Temporary files |
| `/var` | Logs and application data |
| `/mnt` | Mounted drives (Windows drives in WSL) |

---

# 3. Special Symbols

| Symbol | Meaning |
|---------|---------|
| `/` | Root directory |
| `~` | Home directory |
| `.` | Current directory |
| `..` | Parent directory |

Examples

```bash
cd ~
```

```bash
cd ..
```

```bash
cd /
```

---

# 4. WSL Filesystem

Windows drives are mounted inside WSL.

Example

Windows

```text
C:\Users\toutp
```

becomes

```text
/mnt/c/Users/toutp
```

### Recommended Location for New Projects

```text
/home/toutp/projects
```

Reason:

- Better performance
- Better compatibility with Docker
- Better compatibility with Python and Node.js
- Matches production Linux environments

---

# 5. pwd

## Purpose

Print the current working directory.

## Syntax

```bash
pwd
```

## Example

```bash
pwd
```

Output

```text
/home/toutp/projects
```

## Notes

Use this command whenever you are unsure of your current location.

---

# 6. ls

## Purpose

List files and directories.

## Syntax

```bash
ls
```

## Common Options

| Command | Description |
|----------|-------------|
| `ls` | List files and directories |
| `ls -a` | Show hidden files |
| `ls -l` | Long listing format |
| `ls -la` | Long listing including hidden files |
| `ls -lh` | Human-readable file sizes |

## Examples

```bash
ls
```

```bash
ls -la
```

```bash
ls /mnt/c
```

## Notes

One of the most frequently used Linux commands.

---

# 7. cd

## Purpose

Change the current directory.

## Syntax

```bash
cd directory_name
```

## Examples

Go to home directory

```bash
cd ~
```

Go to parent directory

```bash
cd ..
```

Go to root directory

```bash
cd /
```

Go to projects

```bash
cd ~/projects
```

---

# 8. Absolute vs Relative Paths

## Relative Path

Starts from the current directory.

Example

```bash
cd projects
```

---

## Absolute Path

Starts from the root directory.

Example

```bash
cd /home/toutp/projects
```

---

# 9. Best Practices

- Use `pwd` before deleting or moving files.
- Prefer `~/projects` for development projects.
- Use **Tab** for auto-completion.
- Use `ls -la` frequently to inspect directories.
- Learn to navigate using the keyboard instead of a file explorer.

---

# 10. Commands Learned

| Command | Purpose |
|----------|---------|
| `pwd` | Print current directory |
| `ls` | List directory contents |
| `ls -a` | Show hidden files |
| `ls -l` | Long listing |
| `ls -la` | Long listing including hidden files |
| `cd` | Change directory |
| `cd ~` | Go to home directory |
| `cd ..` | Go to parent directory |
| `cd /` | Go to root directory |

---

# Summary

- Linux has a single hierarchical filesystem.
- The root directory is represented by `/`.
- `~` represents my home directory.
- `.` refers to the current directory.
- `..` refers to the parent directory.
- Windows drives are mounted under `/mnt` in WSL.
- I should create new development projects inside `~/projects`.
- `pwd` shows my current location.
- `ls` lists files and directories.
- `cd` changes the current directory.

---


