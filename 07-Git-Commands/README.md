# Git Commands -- Quick Reference

Git commands are grouped below by purpose. Each command includes a short
explanation and an example.

> Replace example names, file paths, branch names, and repository URLs
> with the values used in your project.

## 1. Installation and Configuration

  --------------------------------------------------------------------------------------------
  Command                                                  Purpose
  -------------------------------------------------------- -----------------------------------
  `git --version`                                          Checks the installed Git version.

  `git config --global user.name "Student Name"`           Sets the name recorded as the
                                                           commit author.

  `git config --global user.email "student@example.com"`   Sets the email recorded as the
                                                           commit author.

  `git config --global --list`                             Displays Git configuration values.
  --------------------------------------------------------------------------------------------

Example:

``` bash
git --version
git config --global user.name "Student Name"
git config --global user.email "student@example.com"
git config --global --list
```

These identity settings do not authenticate you to GitHub.

## 2. Creating and Initializing Repositories

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `mkdir my-project`                  Creates a project directory.

  `cd my-project`                     Moves into the project directory.

  `git init`                          Initializes a Git repository in the
                                      current directory.

  `git clone REPOSITORY_URL`          Downloads a remote repository and
                                      its history.
  -----------------------------------------------------------------------

Example:

``` bash
mkdir my-project
cd my-project
git init
```

Clone an existing repository:

``` bash
git clone https://github.com/USERNAME/calculator.git
```

Cloning creates a local repository and normally configures the original
repository as the remote named `origin`.

## 3. Checking Repository Status

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git status`                        Shows untracked files, modified
                                      files, staged changes, and
                                      working-tree status.

  `git branch`                        Lists local branches and marks the
                                      current branch with `*`.

  `git remote -v`                     Lists configured remote connections
                                      and their fetch/push URLs.

  `git ls-files`                      Lists files known to Git in the
                                      index.
  -----------------------------------------------------------------------

Example:

``` bash
git status
git branch
git remote -v
git ls-files
```

Untracked files are normally not shown by `git ls-files`.

## 4. Staging Changes

  Command                       Purpose
  ----------------------------- ------------------------------------------
  `git add main.py`             Stages a specific file.
  `git add .`                   Stages changes in the current directory.
  `git add file1.py file2.py`   Stages multiple selected files.
  `git add *.py`                Stages matching Python files.

Example:

``` bash
git status
git add main.py
git status
```

`git add` stages the file's current contents. If you edit it again after
staging, run `git add` again.

Review staged changes before committing:

``` bash
git diff --staged
```

Avoid accidentally staging sensitive files or generated files.

## 5. Creating and Inspecting Commits

  ------------------------------------------------------------------------
  Command                              Purpose
  ------------------------------------ -----------------------------------
  `git commit -m "Add main program"`   Records staged changes in the local
                                       repository.

  `git log`                            Displays detailed commit history.

  `git log --oneline`                  Displays a compact commit history.
  ------------------------------------------------------------------------

Example:

``` bash
git add main.py
git commit -m "Add main program"
git log --oneline
```

A commit records a staged project snapshot. It includes a unique hash,
author and timestamp, a message, and references to the snapshot and its
parent commit or commits.

Use concise, specific messages, such as:

-   `Add input validation`
-   `Fix division by zero error`
-   `Update project documentation`

Avoid vague messages such as `changes` or `update`.

## 6. Comparing Changes

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git diff`                          Shows tracked changes that have not
                                      been staged.

  `git diff --staged`                 Shows changes staged for commit.

  `git diff HEAD`                     Shows tracked changes relative to
                                      the current commit, including
                                      staged and unstaged changes.
  -----------------------------------------------------------------------

Example:

``` bash
git diff
git diff --staged
git diff HEAD
```

Use these commands to inspect changes and catch unintended edits before
committing.

## 7. Renaming, Removing, and Ignoring Files

  -----------------------------------------------------------------------
  Command or file                     Purpose
  ----------------------------------- -----------------------------------
  `git mv old.py new.py`              Renames or moves a file and stages
                                      the operation.

  `git rm old.py`                     Removes a tracked file from the
                                      working directory and stages the
                                      removal.

  `.gitignore`                        Specifies files and directories
                                      that Git should intentionally
                                      ignore.
  -----------------------------------------------------------------------

Example:

``` bash
git mv old.py new.py
git rm unused.py
```

Example `.gitignore`:

``` gitignore
__pycache__/
*.pyc
.env
*.log
data/
```

Typical items to ignore include temporary files, caches, local
environment configuration, logs, generated outputs, and large datasets
that should not be committed.

## 8. Undoing or Reversing Changes

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git restore --staged main.py`      Unstages a file while preserving
                                      its working-directory edits.

  `git restore main.py`               Discards unstaged modifications to
                                      a tracked file by restoring it from
                                      the index.

  `git revert COMMIT_ID`              Creates a new commit that reverses
                                      the changes introduced by an
                                      earlier commit.
  -----------------------------------------------------------------------

### Unstage a file

``` bash
git restore --staged main.py
```

The staged version is removed from the index, but the working-directory
edits are preserved.

### Discard unstaged changes

``` bash
git diff
git restore main.py
```

**Warning:** `git restore main.py` discards unstaged modifications.
Those changes may be difficult or impossible to recover. Inspect and
save important work first.

### Reverse an earlier commit safely

``` bash
git log --oneline
git revert COMMIT_ID
```

`git revert` preserves the existing commit history and records the
reversal in a new commit. It is often suitable for undoing published
changes.

## 9. Branch Management

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git branch`                        Lists local branches.

  `git branch feature-login`          Creates a branch without switching
                                      to it.

  `git switch feature-login`          Switches to an existing branch.

  `git switch main`                   Switches to the `main` branch.

  `git switch -c feature-login`       Creates a branch and switches to
                                      it.

  `git branch -M main`                Renames the current branch to
                                      `main`.
  -----------------------------------------------------------------------

Example workflow:

``` bash
git branch
git switch -c feature-login
# Make and test changes
git add .
git commit -m "Add login feature"
```

Use descriptive branch names, such as `feature-login`, `fix-navbar`, or
`docs-update`.

Uncommitted changes may prevent switching if they would be overwritten.

## 10. Merging and Rebasing Branches

### Merge

``` bash
git switch main
git merge feature-login
```

Switch to the branch that should receive the changes, then merge the
source branch. Merge combines branch histories and may create a merge
commit.

### Rebase

``` bash
git switch feature-login
git rebase main
```

Rebase replays commits on a new base, rewrites commit identities, and
can produce a linear history.

**Caution:** Avoid rebasing shared commits unless the team understands
the consequences of rewriting history.

### Merge conflict resolution

When Git cannot automatically combine competing changes:

1.  Open the conflicting file.
2.  Decide which change to keep, or combine both.
3.  Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
4.  Stage the resolved file.
5.  Complete the merge and test the result.

Example:

``` bash
git add main.py
```

## 11. Remote Repository Commands

  ----------------------------------------------------------------------------
  Command                                  Purpose
  ---------------------------------------- -----------------------------------
  `git remote add origin REPOSITORY_URL`   Connects the local repository to a
                                           remote repository.

  `git remote -v`                          Lists remote connections.

  `git fetch origin`                       Downloads remote updates without
                                           integrating them into the current
                                           branch.

  `git pull`                               Fetches and integrates updates into
                                           the current branch.

  `git push -u origin main`                Pushes commits to `origin` on
                                           `main` and sets upstream tracking.

  `git push -u origin feature-login`       Pushes a feature branch and sets
                                           upstream tracking.
  ----------------------------------------------------------------------------

Example: connect and publish a local repository.

``` bash
git branch -M main
git remote add origin https://github.com/USERNAME/calculator.git
git push -u origin main
```

Replace the URL with the actual URL of your GitHub repository.

### Fetch vs Pull

-   `git fetch` downloads remote updates but does not integrate them
    into the current branch.
-   `git pull` fetches and integrates updates, typically by merging or
    rebasing according to configuration.

## 12. Tags and Versions

  Command                                  Purpose
  ---------------------------------------- ----------------------------------------
  `git tag`                                Lists tags.
  `git tag -a v1.0.0 -m "Version 1.0.0"`   Creates an annotated tag.
  `git show v1.0.0`                        Displays information about a tag.
  `git push origin v1.0.0`                 Pushes a tag to the remote repository.

Example:

``` bash
git tag
git tag -a v1.0.0 -m "Version 1.0.0"
git show v1.0.0
git push origin v1.0.0
```

A tag identifies a particular point in repository history. Semantic
versioning commonly uses `MAJOR.MINOR.PATCH`.

## 13. Complete Basic Workflows

### A. Start a local project and make the first commit

``` bash
mkdir calculator
cd calculator
git init

# Create or add project files
git status
git add main.py
git status
git commit -m "Add initial calculator"
git log --oneline
```

### B. Upload a local project to GitHub

Create an empty GitHub repository first, then run:

``` bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin REPOSITORY_URL
git push -u origin main
```

### C. Work on a feature branch

``` bash
git switch -c feature-subtraction

# Edit and test files
git add main.py
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction
```

After pushing, open a pull request on GitHub to propose the feature for
review and merging.

### D. Update local main after a pull request is merged

``` bash
git switch main
git pull origin main
```

## 14. Common Git Problems

  -----------------------------------------------------------------------
  Problem                             Possible solution
  ----------------------------------- -----------------------------------
  Untracked files                     Stage required files using
                                      `git add`.

  Push rejected                       Fetch remote changes and integrate
                                      them.

  Merge conflict                      Edit conflicting files and complete
                                      the merge.

  Wrong branch                        Check the current branch using
                                      `git branch`.

  Nothing to commit                   Inspect `git status` and staged
                                      changes.

  Authentication failed               Check credentials and repository
                                      permissions.
  -----------------------------------------------------------------------

When something goes wrong, start by checking:

``` bash
git status
```

## 15. Quick Best Practices

1.  Check `git status` regularly.
2.  Review changes before committing.
3.  Commit changes frequently and logically.
4.  Write clear commit messages.
5.  Use descriptive branch names.
6.  Fetch or pull updates regularly.
7.  Test changes before merging.
8.  Keep passwords, API keys, and private tokens out of repositories.
9.  Use `.gitignore` for files that should not be tracked.
