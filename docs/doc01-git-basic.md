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
