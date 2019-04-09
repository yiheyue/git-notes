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

## Viewing the Commit History

Use `git log` command:

```bash
git log
```

Show difference between the last two entries:

```bash
git log -p -2

# or
git log --patch -2
```

Show abbreviated stats for each commit:

```bash
git log --stat
```

Change the log output:

```bash
# Oneline
git log --pretty=oneline

# Short
git log --pretty=short

# Full
git log --pretty=full

# Fuller
git log --pretty=fuller
```

Specify your own log output:

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

Useful options for `git log --pretty=format`

| Option | Description of Output     |
| ------ | ------------------------- |
| `%H`   | Commit hash               |
| `%h`   | Abbreviated commit hash   |
| `%T`   | Tree hash                 |
| `%t`   | Abbreviated tree hash     |
| `%P`   | Parent hashes             |
| `%p`   | Abbreviated parent hashes |
| `%an`  | Author name               |
| `%ae`  | Author email              |
| `%ad`  | Author date               |
| `%ar`  | Author date, relative     |
| `%cn`  | Committer name            |
| `%ce`  | Committer email           |
| `%cd`  | Committer date            |
| `%cr`  | Committer date, relative  |
| `%s`   | Subject                   |

### Limiting Log Output

Use `-<n>` option:

```bash
# Show the last 3 commits
git log -3
```

Use `--since` or `--until` option:

```bash
git log --since=2.weeks

git log --since="2019-04-08"
```

Options to limit the output of `git log`

| Option                | Description                                                                 |
| --------------------- | --------------------------------------------------------------------------- |
| `-<n>`                | Show only the last n commits                                                |
| `--since`, `--after`  | Limit the commits to those made after the specified date                    |
| `--until`, `--before` | Limit the commits to those made before the specified date                   |
| `--author`            | Only show commits in which the author entry matches the specified string    |
| `--committer`         | Only show commits in which the committer entry matches the specified string |
| `--grep`              | Only show commits with a commit message containing the string               |
| `-S`                  | Only show commits adding or removing code matching the string               |

## Undoing Things

Amend the last commit:

```bash
git commit --amend
```

### Unstaging a Staged File

Use `git reset HEAD <file>` command:

```bash
# Unstage the README.md file
git reset HEAD README.md
```

### Unmodifying a Modified File

Use `git checkout -- <file>` command:

```bash
# Unmodifie the README.md file
git checkout -- README.md
```

## Workign with Remotes

Remote repositories can be on your local machine. The word "remote" does not necessarily imply that the repository is somewhere else on the network or Internet, only that it is elsewhere.

### Showing Your Remotes

Use `git remote` command to show the short output:

```bash
git remote
```

Use `git remote -v` to show the verbose output:

```bash
# Show the URL
git remote -v
```

### Adding Remote Repositories

Use `git remote add <shortname> <url>` to add a new remote Git repository:

```bash
git remote add pb https://github.com/paulboone/ticgit

# Then you can fetch all the information that Paul has but that you do not yet have
git fetch pb
```

### Fetching and Pulling from Your Remotes

Use `git fetch <remote>` to get data from your remote projects:

```bash
git fetch origin
```

> The `git fetch` command only downloads the data to your local repository, it does not automatically merge it with any of your work or modify what you are currently working on.

Use `git pull` command to automatically fetch and then merge that remote branch into your current branch.

### Pushing to Your Remotes

Use `git push <remote> <branch>` to push your data:

```bash
# Push the master branch to origin remote
git push origin master
```

### Inspecting a Remote

Use `git remote show <remote>` to inspect a remote:

```bash
git remote show origin
```

### Renaming and Removing Remotes

Use `git remote rename` command to change a remote's shortname:

```bash
# Rename pb to paul
git remote rename pb paul
```

Use `git remote remove` or `git remote rm` command to remove a remote:

```bash
# Remove a remote called paul
git remote remove paul

# or
git remote rm paul
```

## Tagging

Git has the ability to tag specific points in a repository's history as being important.

### Listing Your Tags

Simple output:

```bash
git tag
```

Use wildcards (requires `-l` or `--list` option):

```bash
git tag -l "v1.8.5*"
```

### Creating Tags

Git supports two types of tags:

- **lightweight**

    A lightweight tag is very much like a branch that does not change, it is just a pointer to a specific commit.

    ```bash
    # Create a lightweight tag
    git tag v1.0.23
    ```

- **annotated**

    Annotated tags are stored as full objects in the Git database. They are checksummed and contain some information of tagging. It is generally recommended.

    ```bash
    # Create an annotated tag
    git tag -a v1.0.0 -m "My version 1.0.0"
    ```

Show the tag data:

```bash
git show v1.0.0
```

### Tagging Later

Just add the checksum after creating tags command:

```bash
git tag -a v0.1 -m "Version 0.1" ab032c1
```

### Sharing Tags

By default, the `git push` command does not transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them.

Push a single tag:

```bash
git push origin v1.4
```

Push all of tags:

```bash
git push --tags
```

### Deleting Tags

Delete a tag on your local repository:

```bash
git tag -d v1.4
```

Delete a tag on remote server

1. Use this format `git push <remote> :refs/tags/<tagname>`

    ```bash
    git push origin :refs/tags/v1.4
    ```

2. Use this format `git push <remote> --delete <tagname>`

    ```bash
    git push origin --delete v1.4
    ```

### Checking out Tags

Example:

```bash
git checkout v1.4
```
