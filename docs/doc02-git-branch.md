# Git Branch

When you make a commit, Git stores a commit object that contains a pointer to the snapshot of the content you staged.

## Branches in a Nutshell

After you make a commit, Git repository will contains some objects:

- **commit**

    The commit object stores a pointer to the tree object.

- **tree**

    The tree object stores a pointer to the blob objects.

- **blob**

    The blob objects represent the contents of one of the files

### Creating a New Branch

Use `git branch <branchname>` command to create a new branch:

```bash
# Create a new branch called testing
git branch testing
```

> The `git branch` command only created a new branch, it did not switch to that branch.

### Switching Branches

Use `git checkout <branchname>` command to switch an existing branch:

```bash
# Switch to testing branch
git checkout testing
```

Creating a new branch and switching to it:

```bash
# Create a new branch called newbranch and switch to it
git checkout -b newbranch
```

### Deleting an Existing Branch

Use `git branch -d <branchname>` command to delete a branch:

```bash
git branch -d issue-53
```

### Merging Branches

Use `git merge <branchname>` command to merge a branch

```bash
# Merge the issue-53 branch
git merge issue-53
```

## Branch Management

List your branches:

```bash
git branch
```

To see the last commit on each branch, run:

```bash
git branch -v
```

To see the merged branches, run:

```bash
git branch --merged
```

To see the unmerged branches, run:

```bash
git branch --no-merged
```
