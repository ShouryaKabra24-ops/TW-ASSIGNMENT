# Git -- Introduction

## 1. What Is Version Control?

Version control is a system that records changes to files over time. It
allows you to inspect, compare, and recover earlier versions.

### Why do we need it?

Without version control, project folders can become confusing:

-   `project.py`
-   `project-final.py`
-   `project-final-new.py`
-   `project-final-latest.py`

Version control helps you:

-   Track file modifications.
-   Identify who made a change and when.
-   Restore earlier versions when necessary.
-   Combine work from multiple contributors.
-   Keep project history organized and manageable.

### Types of Version Control Systems

1.  **Local VCS:** Versions are managed on one computer.
2.  **Centralized VCS:** A central server stores the project history.
    Example: Subversion (SVN).
3.  **Distributed VCS:** Each clone contains repository history.
    Example: Git.

## 2. Introduction to Git

Git is a **distributed version control system** used to track changes in
files and coordinate development.

Important features:

-   Maintains project history through commits.
-   Supports parallel development using branches.
-   Allows local version control without a network.
-   Supports merging contributions from different branches.

### Git vs GitHub

  -----------------------------------------------------------------------
  Git                                 GitHub
  ----------------------------------- -----------------------------------
  Version control system              Hosting and collaboration platform

  Works locally                       Hosts remote repositories

  Tracks project changes              Helps share and review projects

  Local work can be done offline      Online features require
                                      connectivity
  -----------------------------------------------------------------------

**Remember:** Git manages version history. GitHub hosts Git repositories
and provides collaboration features.

## 3. How Git Works

Git records project changes as a sequence of commits.

A typical sequence might be:

`Initial Code → Bug Fix → New Feature`

Git manages changes in these steps:

1.  Files are modified in the working directory.
2.  Selected changes are added to the staging area.
3.  A commit records the staged changes.
4.  Git maintains a history that can be inspected later.

A **commit** represents a recorded project snapshot, not simply a backup
of an individual file.

## 4. Git Architecture and Main Areas

Git supports local development and collaboration through remote
repositories.

  -----------------------------------------------------------------------
  Area                                Meaning
  ----------------------------------- -----------------------------------
  Working directory                   Files currently being edited

  Staging area                        Changes selected for the next
                                      commit

  Local repository                    Committed project history stored
                                      locally

  Remote repository                   Shared repository hosted on a
                                      server, such as GitHub
  -----------------------------------------------------------------------

The basic flow is:

`Working Directory → Staging Area → Local Repository → Remote Repository`

-   `git add` moves selected changes to the staging area.
-   `git commit` records staged changes in the local repository.
-   `git push` sends local commits to a remote repository.

## 5. Installing and Configuring Git

Git can be installed on Windows, Linux, and macOS.

-   **Windows:** Download Git from
    [git-scm.com/downloads](https://git-scm.com/downloads).

-   **Ubuntu/Debian:**

    ``` bash
    sudo apt update
    sudo apt install git
    ```

-   **macOS (Homebrew):**

    ``` bash
    brew install git
    ```

After installation, open a terminal or Git Bash.

### Verify the installation

``` bash
git --version
```

The output displays the installed Git version.

### Configure your identity

Git uses these values to identify the author of commits:

``` bash
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
```

Check the configuration:

``` bash
git config --global --list
```

These values identify the commit author; they do not authenticate you to
GitHub.

## 6. Git Repositories

A **Git repository** stores project history and the information needed
to track changes.

A project might contain:

-   `main.py`
-   `README.md`
-   `data.csv`
-   `requirements.txt`

Git stores repository metadata in the hidden `.git` directory.

### Create a repository

``` bash
mkdir my-project
cd my-project
git init
```

-   `mkdir` creates a directory.
-   `cd` changes the current directory.
-   `git init` initializes a Git repository in the current directory.

## 7. Staging and Commits

### The three main areas

1.  **Working directory:** Where files are edited.
2.  **Staging area:** Where changes are selected for the next commit.
3.  **Repository:** Where committed project history is stored.

### Check repository status

``` bash
git status
```

This displays:

-   Untracked files.
-   Modified files.
-   Staged changes ready to commit.
-   Whether the working tree is clean.

### Stage changes

``` bash
git add main.py
```

To stage all changes in the current directory:

``` bash
git add .
```

You can also stage selected files:

``` bash
git add file1.py file2.py
```

`git add` stages the file's current contents. If you edit the file again
after staging it, stage it again before committing.

### Create a commit

``` bash
git add main.py
git commit -m "Add main program"
```

A commit includes a unique identifier (hash), author and timestamp, a
commit message, and references to the recorded project snapshot and its
parent commit or commits.

Good commit messages are concise and specific. For example:

-   `Add input validation`
-   `Fix division by zero error`
-   `Update project documentation`

Avoid vague messages such as `changes` or `update`.

## 8. Viewing and Comparing Project History

View commit history:

``` bash
git log
```

View a compact history:

``` bash
git log --oneline
```

Each compact entry shows an abbreviated commit hash and its message.

Compare changes:

``` bash
git diff
git diff --staged
git diff HEAD
```

-   `git diff` shows changes not yet staged.
-   `git diff --staged` shows changes staged for commit.
-   `git diff HEAD` shows tracked changes relative to the current
    commit, including staged and unstaged changes.

Inspect files known to Git:

``` bash
git ls-files
```

This lists files in Git's index; untracked files are normally not shown.

## 9. Branches

A **branch** is an independent line of development. It allows changes to
be made without directly modifying another branch.

-   The `main` branch usually contains the primary project history.
-   A feature branch isolates new development.
-   Branches can later be merged.

### Why use branches?

-   Develop features independently.
-   Fix bugs separately.
-   Keep the main branch stable.
-   Review changes before merging.

A branch is a movable reference to a commit, not a separate copy of the
entire project.

### Create and list branches

``` bash
git branch
git branch feature-login
```

`git branch` lists local branches. The current branch is marked with an
asterisk. Creating a branch does not automatically switch to it.

### Switch branches

``` bash
git switch feature-login
git switch main
```

Create a branch and switch to it in one command:

``` bash
git switch -c feature-login
```

Use descriptive names such as `feature-login`, `fix-navbar`, or
`docs-update`.

### Merge branches

Switch to the branch that should receive the changes, then merge the
source branch:

``` bash
git switch main
git merge feature-login
```

The currently checked-out branch is the target branch.

### Merge conflicts

A merge conflict occurs when Git cannot automatically combine competing
changes. For example, two developers may edit the same line in `main.py`
differently.

To resolve a conflict:

1.  Open the conflicting file.
2.  Decide which change to keep, or combine both.
3.  Remove the conflict markers (`<<<<<<<`, `=======`, and `>>>>>>>`).
4.  Stage the resolved file and complete the merge.
5.  Test the result.

A conflict is a request for a person or tool to resolve competing
changes; it does not necessarily mean the repository is damaged.

## 10. Git Best Practices

1.  Commit changes frequently and logically.
2.  Write clear, specific commit messages.
3.  Use descriptive branch names.
4.  Review changes before committing.
5.  Fetch or pull updates regularly.
6.  Test changes before merging.
7.  Keep credentials and unnecessary generated files out of the
    repository.
8.  Document projects using a README.

A clean repository history makes collaboration, debugging, and
maintenance easier.
