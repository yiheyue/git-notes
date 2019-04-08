# Git Basics

## Getting a Git Repository

There are two ways to get a Git repository:

1. Initialize a directory, turn it into a Git repository

2. Clone an existing Git repository

### Initialize a directory

1. Change directory

    ```bash
    cd <dirname>
    ```

2. Initialize it

    ```bash
    git init
    ```

3. Track all of files inside it

    ```bash
    git add .
    git commit -m "Initial commit"
    ```

### Glone an existing Git repository

Use `git clone <url>`

```bash
git clone https://github.com/libgit2/libgit2
```

Specify the new directory name

```bash
git clone https://github.com/libgit2/libgit2 my-libgit
```

## Recording Changes to the Repository

Each file in your working directory can be in one of two states:

- **tracked**

    Tracked files are files that were in the last snapshot. They are files that Git knows about.

- **untracked**

    Untracked files are files that were not in your last snapshot and are not in your staging area.

### Checking the Status of Your Files

Use `git status` command:

```bash
git status
```

### Tracking New Files

Use `git add` command:

```bash
# Track README file
git add README
```

### Staging Modified Files

Use `git add` command:

```bash
# Stage a modified file (CONFIG)
git add CONFIG
```

### Short Status

Use `git status -s` or `git status --short` command:

```bash
git status -s
```

### Ignoring Files

Create a file named `.gitignore`

Example:

```
# Ignore files ending in ".o" or ".a"
*.[oa]
```

Rules in the `.gitignore`:

- Blank lines or lines starting with `#` are ignored.

- Standard glob patterns work, and will be applied recursively throughout the entire working tree.

- You can start patterns with a forward slash (`/`) to avoid recursivity.

- You can end patterns with a forward slash (`/`) to spcify a directory.

- You can negate a pattern by starting it with an exclamation point (`!`).

### Viewing Your Staged and Unstaged Changes

To see what you have changed but not yet staged:

```bash
# This command compares what is in your working directory with what is in your staging area.
git diff
```

To see what you haved staged that will go into your next commit:

```bash
# This command compares your staged changes to your last command.
git diff --staged

# or (--staged and --cached are synonyms)
git diff --cached
```

### Committing Your Changes

Use `git commit` command or

Use `git commit -m "commit message"`

### Removing Files

Use `git rm` command:

```bash
# Remove README file
git rm README
```

Remove the file in the stage area:

```bash
# Remove README file from stage area
git rm --cached README
```

### Moving Files

Use `git mv` command:

```bash
# Rename file-a to file-a-mv
git mv file-a file-a-mv
```

This is equivalent to running something like this:

```bash
mv file-a file-a-mv

git rm file-a

git add file-a-mv
```
