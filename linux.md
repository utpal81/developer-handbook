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

##  Objectives

After completing this section, I should be able to:

- Explain the Linux filesystem hierarchy.
- Navigate directories using the terminal.
- Understand the difference between absolute and relative paths.
- Use `pwd`, `ls`, and `cd` confidently.
- Understand the meaning of `/`, `~`, `.`, and `..`.

---

# I. Linux Filesystem

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

# II. Important Directories

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

# III. Special Symbols

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

# IV. WSL Filesystem

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

# V. pwd

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

# VI. ls

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

# VII. cd

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

# VIII. Absolute vs Relative Paths

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

# Best Practices

- Use `pwd` before deleting or moving files.
- Prefer `~/projects` for development projects.
- Use **Tab** for auto-completion.
- Use `ls -la` frequently to inspect directories.
- Learn to navigate using the keyboard instead of a file explorer.

---

# Commands Learned

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
---
---
---
---

# 2 - Working with Files & Directories

## Objectives

After completing this section, I should be able to:

- Create files and directories.
- Create nested directory structures.
- Copy files and directories.
- Move and rename files.
- Delete files and directories safely.
- Understand the difference between copying and moving.

---

# I. mkdir

## Purpose

Create one or more directories.

## Syntax

```bash
mkdir directory_name
```

## Examples

Create a single directory

```bash
mkdir projects
```

Create multiple directories

```bash
mkdir ai react fastapi practice
```

Create nested directories

```bash
mkdir -p ~/projects/ai/rag-chatbot
```

## Notes

The `-p` option creates parent directories automatically if they do not already exist.

---

# II. touch

## Purpose

Create an empty file.

## Syntax

```bash
touch filename
```

## Examples

Create a Python file

```bash
touch app.py
```

Create multiple files

```bash
touch README.md requirements.txt main.py
```

## Notes

If the file already exists, `touch` updates its modification timestamp.

---

# III. cp

## Purpose

Copy files or directories.

## Syntax

Copy a file

```bash
cp source destination
```

Copy a directory

```bash
cp -r source_directory destination_directory
```

## Examples

Copy a file

```bash
cp app.py backup.py
```

Copy a directory

```bash
cp -r ai ai_backup
```

## Notes

Use the `-r` option when copying directories.

---

# IV. mv

## Purpose

Move or rename files and directories.

## Syntax

```bash
mv source destination
```

## Examples

Rename a file

```bash
mv app.py main.py
```

Move a file into another directory

```bash
mv main.py src/
```

Rename a directory

```bash
mv old_project new_project
```

## Notes

`mv` is used for both moving and renaming.

---

# V. rm

## Purpose

Delete files.

## Syntax

```bash
rm filename
```

## Example

```bash
rm notes.txt
```

## Notes

Deleted files are **not** moved to the Recycle Bin.

Be careful.

---

# VI. rmdir

## Purpose

Delete an empty directory.

## Syntax

```bash
rmdir directory_name
```

## Example

```bash
rmdir practice
```

## Notes

The directory must be empty.

---

# VII. rm -r

## Purpose

Delete a directory and everything inside it.

## Syntax

```bash
rm -r directory_name
```

## Example

```bash
rm -r practice
```

## Notes

⚠️ This permanently deletes the directory and all of its contents.

Always verify your current directory using:

```bash
pwd
```

before using this command.

---

# VIII. Difference Between cp and mv

| cp | mv |
|----|----|
| Copies files | Moves files |
| Original remains | Original is removed |
| Creates duplicate | Transfers the original |

Example

```bash
cp app.py backup.py
```

Results

```
app.py
backup.py
```

Example

```bash
mv app.py main.py
```

Results

```
main.py
```

---

# Best Practices

- Check your current directory using `pwd`.
- Use meaningful directory names.
- Keep projects inside `~/projects`.
- Be extremely careful with `rm -r`.
- Use `cp` before making major changes to important files.

---

# Commands Learned

| Command | Purpose |
|----------|---------|
| `mkdir` | Create directory |
| `mkdir -p` | Create nested directories |
| `touch` | Create empty file |
| `cp` | Copy files |
| `cp -r` | Copy directories |
| `mv` | Move or rename |
| `rm` | Delete files |
| `rmdir` | Delete empty directory |
| `rm -r` | Delete directory recursively |

---

# Practice Lab

Create the following structure using only the terminal.

```
practice/
└── linux/
    ├── README.md
    ├── notes.txt
    ├── commands.txt
    ├── practice.py
    └── examples/
```

Tasks

1. Create all directories.
2. Create all files.
3. Rename `commands.txt` to `linux_commands.txt`.
4. Copy `practice.py` to `practice_backup.py`.
5. Move `practice_backup.py` into `examples/`.
6. Display the final directory structure.

---

# Summary

- `mkdir` creates directories.
- `mkdir -p` creates nested directories.
- `touch` creates empty files.
- `cp` copies files or directories.
- `mv` moves or renames files and directories.
- `rm` deletes files.
- `rmdir` deletes empty directories.
- `rm -r` deletes directories recursively.
- Always verify your current location using `pwd`.

---
---
---
---
---
# 3 - Viewing & Searching Files

## Objectives

After completing this section, I should be able to:

- View the contents of files.
- Read large files efficiently.
- Display specific lines from a file.
- Search for files.
- Search for text inside files.
- Locate installed commands.

---

# I. cat

## Purpose

Display the contents of a file.

## Syntax

```bash
cat filename
```

## Example

```bash
cat README.md
```

## Create and Display a File

```bash
echo "Hello Linux" > hello.txt
cat hello.txt
```

Output

```text
Hello Linux
```

## Notes

Best suited for small files.

---

# II. less

## Purpose

View large files one page at a time.

## Syntax

```bash
less filename
```

## Example

```bash
less linux.md
```

## Navigation

| Key | Action |
|------|--------|
| Space | Next page |
| b | Previous page |
| ↑ ↓ | Scroll |
| /text | Search |
| n | Next match |
| q | Quit |

## Notes

Preferred over `cat` for large files.

---

# III. head

## Purpose

Display the beginning of a file.

## Syntax

```bash
head filename
```

## Example

```bash
head linux.md
```

Display first 20 lines

```bash
head -20 linux.md
```

---

# IV. tail

## Purpose

Display the end of a file.

## Syntax

```bash
tail filename
```

## Example

```bash
tail linux.md
```

Display last 20 lines

```bash
tail -20 linux.md
```

### Follow a growing file

```bash
tail -f logfile.log
```

Press

```
Ctrl + C
```

to stop.

## Notes

Very useful for viewing application logs.

---

# V. find

## Purpose

Search for files and directories.

## Syntax

```bash
find location criteria
```

## Examples

Find Python files

```bash
find . -name "*.py"
```

Find README files

```bash
find . -name "README.md"
```

Find directories

```bash
find . -type d
```

Find files

```bash
find . -type f
```

## Notes

`.` means the current directory.

---

# VI. grep

## Purpose

Search for text inside files.

## Syntax

```bash
grep "text" filename
```

## Examples

Search for "Linux"

```bash
grep "Linux" linux.md
```

Search recursively

```bash
grep -r "FastAPI" .
```

Ignore case

```bash
grep -i "linux" linux.md
```

Display line numbers

```bash
grep -n "Lesson" linux.md
```

## Notes

One of the most useful Linux commands for developers.

---

# VII. which

## Purpose

Locate an executable command.

## Syntax

```bash
which command
```

## Examples

```bash
which python3
```

```bash
which git
```

```bash
which node
```

Output

```text
/usr/bin/python3
```

## Notes

Useful for checking which version of a program is being used.

---

# Command Comparison

| Command | Purpose |
|----------|---------|
| `cat` | Display entire file |
| `less` | Read large files |
| `head` | Display beginning of file |
| `tail` | Display end of file |
| `find` | Search for files |
| `grep` | Search inside files |
| `which` | Locate installed command |

---

# Best Practices

- Use `cat` for small files.
- Use `less` for large files.
- Use `head` to inspect the beginning of a file.
- Use `tail -f` when monitoring log files.
- Use `find` instead of manually searching directories.
- Use `grep` to search code and logs efficiently.
- Use `which` when multiple versions of software might be installed.

---

# Practice Lab

Go to your practice directory.

```bash
cd ~/projects/practice/linux
```

### Step 1

Add text to a file.

```bash
echo "Linux is awesome." > notes.txt
echo "FastAPI is a Python framework." >> notes.txt
echo "React is a frontend library." >> notes.txt
```

### Step 2

View the file.

```bash
cat notes.txt
```

### Step 3

Display the first two lines.

```bash
head -2 notes.txt
```

### Step 4

Display the last line.

```bash
tail -1 notes.txt
```

### Step 5

Search for the word "Python".

```bash
grep "Python" notes.txt
```

### Step 6

Search all Python files.

```bash
find . -name "*.py"
```

### Step 7

Find where Git is installed.

```bash
which git
```

### Step 8

Find where Python is installed.

```bash
which python3
```

---

# Summary

- `cat` displays an entire file.
- `less` is used to read large files.
- `head` displays the beginning of a file.
- `tail` displays the end of a file.
- `find` searches for files and directories.
- `grep` searches for text within files.
- `which` locates executable programs.

---
---
---
---
---
# 4 - File Permissions & Ownership

## Objectives

After completing this section, I should be able to:

- Understand Linux file permissions.
- Read the permission string shown by `ls -l`.
- Understand users, groups, and others.
- Change file permissions using `chmod`.
- Change file ownership using `chown`.
- Understand when and why to use `sudo`.

---

# I. Why File Permissions Matter

Linux is a multi-user operating system.

Every file and directory belongs to a user and has permissions that determine:

- Who can read it
- Who can modify it
- Who can execute it

Example

```text
-rwxr-xr--
```

This single line tells Linux exactly who can do what with the file.

---

# II. Viewing Permissions

Use

```bash
ls -l
```

Example

```text
-rwxr-xr-- 1 toutp toutp 245 Jul 5 app.py
```

Let's decode it.

```
-rwxr-xr--
│││ │ │
│││ │ └── Others
│││ └──── Group
│└────── Owner
└──────── File Type
```

---

# III. File Types

The first character indicates the type.

| Symbol | Meaning |
|----------|---------|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |

Examples

```text
-rw-r--r--
```

Regular file

```text
drwxr-xr-x
```

Directory

---

# IV. Permission Symbols

There are three permissions.

| Symbol | Meaning |
|----------|---------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |

---

# V. Owner, Group, Others

Permissions are divided into three categories.

```
-rwxr-xr--
```

Split into groups.

```
rwx  r-x  r--
│     │     │
│     │     └── Others
│     └──────── Group
└────────────── Owner
```

Owner

Usually you.

Group

People belonging to the same group.

Others

Everyone else.

---

# VI. Meaning of Each Permission

## Read (r)

Can open and read the file.

---

## Write (w)

Can modify or delete the file.

---

## Execute (x)

Can run the file as a program.

Example

```bash
./script.sh
```

---

# VII. Numeric Permissions

Linux also represents permissions using numbers.

| Permission | Value |
|------------|------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Add them together.

| Permission | Number |
|------------|--------|
| rwx | 7 |
| rw- | 6 |
| r-x | 5 |
| r-- | 4 |

---

## Example

```
755
```

Means

```
Owner : rwx

Group : r-x

Others: r-x
```

---

```
644
```

Means

```
Owner : rw-

Group : r--

Others: r--
```

---

# VIII. chmod

## Purpose

Change file permissions.

## Syntax

```bash
chmod permissions filename
```

Examples

```bash
chmod 755 script.sh
```

```bash
chmod 644 notes.txt
```

---

# IX. Symbolic chmod

Instead of numbers, you can use letters.

Add execute permission

```bash
chmod +x script.sh
```

Remove execute permission

```bash
chmod -x script.sh
```

Owner gets write permission

```bash
chmod u+w notes.txt
```

Group loses write permission

```bash
chmod g-w notes.txt
```

Others get read permission

```bash
chmod o+r notes.txt
```

---

# X. chown

## Purpose

Change file ownership.

Syntax

```bash
sudo chown owner filename
```

Example

```bash
sudo chown toutp app.py
```

Owner and group

```bash
sudo chown toutp:developers app.py
```

---

# XI. sudo

## Purpose

Run a command with administrator privileges.

Example

```bash
sudo apt update
```

You'll be asked for your password.

---

# XII. Common Permission Values

| Number | Meaning |
|----------|---------|
| 777 | Everyone has full access |
| 755 | Owner full access, others read & execute |
| 700 | Only owner has access |
| 644 | Owner can edit, others can read |
| 600 | Only owner can read/write |

---

#  Best Practices

✅ Use

```
644
```

for normal files.

---

Use

```
755
```

for executable scripts.

---

Avoid

```
777
```

unless absolutely necessary.

---

Use

```bash
chmod +x
```

for shell scripts.

---

Use

```bash
ls -l
```

to verify permissions.

---

# Commands Learned

| Command | Purpose |
|----------|---------|
| `ls -l` | View permissions |
| `chmod` | Change permissions |
| `chmod +x` | Make executable |
| `chmod 755` | Set numeric permissions |
| `chown` | Change owner |
| `sudo` | Execute as administrator |

---

# Practice Lab

Create a file.

```bash
touch script.sh
```

View permissions.

```bash
ls -l
```

Make it executable.

```bash
chmod +x script.sh
```

Verify.

```bash
ls -l
```

Remove execute permission.

```bash
chmod -x script.sh
```

Verify again.

```bash
ls -l
```

---

# Summary

- Linux protects files using permissions.
- Permissions are assigned to the owner, group, and others.
- The three permissions are read (`r`), write (`w`), and execute (`x`).
- `chmod` changes permissions.
- `chown` changes ownership.
- `sudo` runs commands with administrator privileges.
- `755` and `644` are the most commonly used permission sets.

---
---
---
---
---

# 5 - Processes & Jobs

## Objectives

After completing this lesson, I should be able to:

- Understand what a process is.
- Understand what a job is.
- View running processes.
- Monitor system resources.
- Stop processes safely.
- Run programs in the background.
- Suspend and resume programs.
- Find process IDs (PIDs).

---

# I. What is a Process?

A **process** is simply a **running program**.

Examples

- VS Code
- Google Chrome
- Python
- FastAPI
- React Development Server
- Docker

Every running application is a process.

Example

```bash
python app.py
```

When this command starts, Linux creates a new process.

---

# II. What is a Job?

A **job** is a process that is managed by the current shell (terminal).

Example

```bash
python app.py
```

Press

```
Ctrl + Z
```

The process is suspended.

Now run

```bash
jobs
```

Output

```
[1]+ Stopped python app.py
```

This suspended process is now called a **job**.

---

# Process vs Job

| Process | Job |
|----------|-----|
| Managed by the operating system | Managed by the shell |
| Exists whether terminal is open or not | Exists only in the current shell |
| Identified by PID | Identified by Job Number |

---

# III. Process ID (PID)

Every process has a unique Process ID.

Example

```
PID

3154

9201

10452
```

Linux uses the PID to identify running processes.

---

# IV. ps

## Purpose

Display running processes.

## Syntax

```bash
ps
```

Example

```bash
ps
```

Typical Output

```
PID TTY          TIME CMD
3456 pts/0    00:00:00 bash
4123 pts/0    00:00:00 python
```

---

## More Useful

```bash
ps aux
```

Shows all running processes.

---

# V. top

## Purpose

Real-time process monitor.

Run

```bash
top
```

Shows

- CPU usage
- Memory usage
- Running processes
- Load average

Quit using

```
q
```

---

# VI. htop

A more user-friendly version of `top`.

Install

```bash
sudo apt install htop
```

Run

```bash
htop
```

Exit

```
F10
```

---

# VII. pgrep

Find the PID of a running process.

Example

```bash
pgrep python
```

Output

```
5312
```

---

# VIII. kill

Stop a running process.

Syntax

```bash
kill PID
```

Example

```bash
kill 5312
```

Linux sends a signal asking the process to terminate.

---

# IX. kill -9

Forcefully terminate a process.

Example

```bash
kill -9 5312
```

Use only if the process refuses to stop.

---

# X. killall

Stop every process with the same name.

Example

```bash
killall python
```

---

# XI. Running Programs in the Background

Example

```bash
python app.py &
```

The ampersand (`&`) starts the process in the background.

You immediately get your terminal back.

---

# XII. jobs

View background and suspended jobs.

```bash
jobs
```

Example

```
[1]+ Running python app.py &
```

---

# XIII. Ctrl + Z

Suspend the current process.

Example

```bash
python app.py
```

Press

```
Ctrl + Z
```

Output

```
Stopped
```

The process is paused, not terminated.

---

# XIV. bg

Resume a suspended job in the background.

```bash
bg
```

---

# XV. fg

Bring a background job back to the foreground.

```bash
fg
```

---

# XVI. Ctrl + C

Terminate the running foreground process.

Example

```bash
python app.py
```

Press

```
Ctrl + C
```

The process exits.

This is the most common way to stop a program.

---

# Commands Learned

| Command | Purpose |
|----------|---------|
| `ps` | View running processes |
| `ps aux` | View all processes |
| `top` | Monitor processes |
| `htop` | Interactive process viewer |
| `pgrep` | Find process ID |
| `kill` | Stop process |
| `kill -9` | Force stop process |
| `killall` | Stop all matching processes |
| `jobs` | View shell jobs |
| `bg` | Resume job in background |
| `fg` | Bring job to foreground |

---

# Best Practices

- Use `Ctrl + C` to stop a program normally.
- Use `kill` only if necessary.
- Use `kill -9` only as a last resort.
- Use `htop` when troubleshooting performance.
- Learn to use `jobs`, `bg`, and `fg` for multitasking in the terminal.

---

# Practice Lab

## Exercise 1

Run

```bash
sleep 100
```

Press

```
Ctrl + Z
```

View jobs

```bash
jobs
```

Resume

```bash
bg
```

Bring back

```bash
fg
```

Terminate

```
Ctrl + C
```

---

## Exercise 2

Run

```bash
sleep 300 &
```

Find it

```bash
jobs
```

Find its PID

```bash
pgrep sleep
```

Terminate it

```bash
kill PID
```

---

## Exercise 3

Open another terminal.

Run

```bash
top
```

Observe

- CPU usage
- Memory usage
- Running processes

Exit

```
q
```

---

# Summary

- Every running program is a process.
- Every process has a PID.
- Jobs are processes managed by the current shell.
- `Ctrl + C` terminates a program.
- `Ctrl + Z` suspends a program.
- `bg` resumes a job in the background.
- `fg` brings it back to the foreground.
- `kill` stops a process.
- `top` monitors system activity.

---




