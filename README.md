# Git Notes

## VCS

- VCS - Version Control System

### Local Version Control

One of the most popular VCS tools was a system called RCS, which is still distributed with many computers today.

### Centralized Version Control Systems

- CVS

- Subversion

- Perforce

### Distributed Version Control Systems

- Git

- Mercurial

- Bazaar

- Darcs

## What is Git?

- Snapshots, not differences

- Nearly every operation is local

- Git has integrity

    The mechanism that Git uses for this checksumming is called a SHA-1 hash. It is a 40-character string.

    ```
    24b9da6552252987aa493b52f8696cd6d3b00373
    ```

- Git generally only adds data

- The three states

    - **committed**

        Committed means that the data is safely stored in your local database.

    - **modified**

        Modified means that you have changed the file but have not committed it to your database yet.

    - **staged**

        Staged means that you have marked a modified file in its current version to go into your next commit snapshot.

## First-Time Git Setup

Git configuration variables can be stored in three different places:

1. `/etc/gitconfig`

    This file contains values applied to every user on the system and all their repositories.

    ```bash
    # Passing --system option to read/write this file
    git config --system
    ```

2. `~/.gitconfig` or `~/.config/git/config`

    This file affects all of the repositories you work with on your system.

    ```bash
    # Passing --global option to read/write this file
    git config --global
    ```

3. `config`

    This file in the Git directory (`.git/config`). It affects the specific single repository that you are working with.

    ```bash
    # Passing --local option to read/write this file
    git config --local
    ```
