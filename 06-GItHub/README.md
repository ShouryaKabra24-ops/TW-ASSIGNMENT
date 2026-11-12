# GitHub -- Introduction and Collaboration

## 1. What Is GitHub?

GitHub is an online platform for hosting Git repositories and
collaborating on software projects.

Major features include:

-   Hosting and sharing source code.
-   Maintaining project history through Git.
-   Collaborating with other developers.
-   Reviewing code using pull requests.
-   Tracking bugs and tasks using Issues.

**Remember:** Git manages version history; GitHub provides hosting and
collaboration features around Git repositories.

## 2. Git vs GitHub

  -----------------------------------------------------------------------
  Git                                 GitHub
  ----------------------------------- -----------------------------------
  Version control system              Hosting and collaboration platform

  Runs locally                        Provides remote hosting

  Tracks file changes                 Helps share and collaborate on
                                      projects

  Maintains commits                   Displays repository history

  Supports branches and merges        Supports pull requests, reviews,
                                      and Issues
  -----------------------------------------------------------------------

Example: Use Git to commit changes on your computer and GitHub to share
those commits with your project team.

## 3. Creating a GitHub Account

1.  Visit [github.com](https://github.com/).
2.  Create an account using an email address.
3.  Verify the email address if prompted.
4.  Enable two-factor authentication for better security.
5.  Sign in and open your profile.

**Security tip:** Never share passwords, personal access tokens, or
private SSH keys with other people.

## 4. Creating a GitHub Repository

A repository stores a project's files and Git history.

1.  Sign in to GitHub.
2.  Select **New repository**.
3.  Enter a repository name, such as `calculator`.
4.  Choose public or private visibility.
5.  Optionally add a README and `.gitignore`.
6.  Select **Create repository**.

### Public vs Private

-   **Public:** Anyone can view the repository.
-   **Private:** Access is limited to authorized users.

A GitHub repository page commonly provides access to:

-   **Code:** Project files and directories.
-   **Issues:** Bug reports and task discussions.
-   **Pull requests:** Proposed changes and reviews.
-   **Actions:** Automated workflows and testing.
-   **Settings:** Repository permissions and configuration.

## 5. Understanding README.md

A README introduces the project and explains how to use it. GitHub
displays it on the repository page.

A useful README may include:

-   Project purpose and features.
-   Installation requirements.
-   Usage instructions and examples.
-   Contributors and licensing information.

### Example README

``` markdown
# Calculator

A simple Python calculator.

## Features
- Addition
- Subtraction

## Run
python main.py
```

Use Markdown headings (`#`, `##`) and bullet points (`-`) to keep the
document readable.

## 6. Uploading a Local Project to GitHub

You can publish a project that already exists on your computer.

### Step 1: Create a repository on GitHub

Create a repository named `calculator`. For the workflow below, create
it empty (do not initialize it with a README).

### Step 2: Initialize and commit locally

Open a terminal inside your project directory:

``` bash
git init
git add .
git commit -m "Initial commit"
```

### Step 3: Connect the local repository to GitHub

Copy the repository URL from GitHub and run:

``` bash
git branch -M main
git remote add origin REPOSITORY_URL
```

Replace `REPOSITORY_URL` with the actual URL of your repository.

### Step 4: Push the project

``` bash
git push -u origin main
```

This sends local commits to the remote repository. The `-u` option sets
the upstream tracking relationship.

The repository must have a configured remote, and you must have the
required authentication and permissions.

### Check the remote

``` bash
git remote -v
```

This lists configured remote connections. `origin` is the conventional
name for the remote.

## 7. Cloning a GitHub Repository

Cloning creates a local copy of a remote repository, including its Git
history.

``` bash
git clone REPOSITORY_URL
```

Cloning typically:

-   Downloads the repository's files and history.
-   Creates a local repository.
-   Configures the original repository as a remote named `origin`.
-   Sets up local references to remote branches.

## 8. Getting Updates from GitHub

### Fetch

``` bash
git fetch origin
```

Downloads remote updates without integrating them into the current
branch.

### Pull

``` bash
git pull
```

Fetches updates and integrates them into the current branch, typically
by merging or rebasing according to configuration.

**Difference:** Fetch lets you inspect remote updates first; pull also
attempts to integrate them into your current branch.

## 9. Collaboration with Branches and Pull Requests

A common collaborative workflow is:

1.  Create a branch for a feature or fix.
2.  Edit and test the code.
3.  Stage and commit the changes.
4.  Push the branch to GitHub.
5.  Open a pull request (PR).
6.  Request review and address feedback.
7.  Merge the approved changes.

### What Is a Pull Request?

A pull request proposes changes for review and integration into another
branch on a hosting platform such as GitHub.

Typical process:

1.  Push a feature branch to GitHub.
2.  Open a pull request against the target branch.
3.  Explain the changes and their purpose.
4.  Request reviews and run checks.
5.  Address feedback and merge when approved.

A pull request supports discussion and review; it is not the same as the
local `git pull` command.

### Code review

-   **Reviewer:** Checks correctness, identifies potential bugs,
    suggests improvements, and verifies tests and readability.
-   **Contributor:** Explains the changes, responds to feedback, updates
    the branch, and verifies the final result.

Keep pull requests focused, small enough to review, and supported by
relevant tests.

## 10. Forking a Repository

A **fork** is a separate repository copy under another account or
namespace on a hosting platform.

Forks allow contributors to:

-   Work independently on a copy of a project.
-   Contribute to projects they do not own.
-   Propose changes through pull requests.

A common contribution flow is:

1.  Fork a public project on GitHub.
2.  Clone your fork to your computer.
3.  Make and commit changes.
4.  Push the changes to your fork.
5.  Propose them to the original project through a pull request.

### Fork vs Clone

  -----------------------------------------------------------------------
  Fork                                Clone
  ----------------------------------- -----------------------------------
  Creates a separate hosted           Creates a local repository copy
  repository copy                     

  Located on GitHub or another        Located on your computer
  hosting platform                    

  Supports independent contribution   Supports local development
  -----------------------------------------------------------------------

## 11. Issues and Projects

### GitHub Issues

Issues help teams discuss and track bugs, features, questions, and
project tasks.

Common uses:

-   Report a software bug.
-   Suggest a new feature.
-   Assign tasks to contributors.
-   Discuss requirements and possible solutions.

Example:

-   **Title:** Calculator crashes for zero division
-   **Description:** Handle division by zero and display an appropriate
    error message.

### GitHub Projects

GitHub Projects provides tools for organizing work and tracking project
progress.

Example task statuses:

  Status        Example task
  ------------- ------------------------------
  Todo          Design calculator interface
  In Progress   Implement division operation
  In Review     Review input validation
  Done          Write project README

Projects can organize work using tables or board views, track progress,
and link tasks to Issues and pull requests.

## 12. Tags and Releases

A Git tag identifies a particular point in repository history, often to
mark a software version.

Semantic versioning commonly uses:

`MAJOR.MINOR.PATCH`

GitHub Releases can attach notes and downloadable files to a version
tag.

## 13. Authentication and Security

-   Use HTTPS or SSH to connect to GitHub.
-   Configure a personal access token when required for HTTPS
    authentication.
-   Use SSH keys securely when choosing SSH.
-   Never commit passwords, API keys, or private tokens.
-   Use `.gitignore` for sensitive local configuration files.
-   Review repository visibility and access permissions.

**Important:** Adding a secret to `.gitignore` does not remove it from
Git history if it has already been committed.

## 14. Collaboration Best Practices

1.  Use branches to isolate work.
2.  Keep commits focused and write clear messages.
3.  Review changes before merging.
4.  Keep pull requests small and focused.
5.  Test changes before merging.
6.  Keep credentials out of repositories.
7.  Document projects using a README.
