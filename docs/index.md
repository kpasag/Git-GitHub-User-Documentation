# Introduction

The purpose of this document is to help you learn [**Git**](https://git-scm.com/) and [**GitHub**](https://github.com/) for COMP 1800 and future projects.

> :simple-git: [**Git**](https://git-scm.com/) is an open-source version control software that lets you keep track of changes you have made in source code or other files during development.
> 
> :simple-github: [**GitHub**](https://github.com/) is a cloud service platform that acts as a remote storage and hosting service for Git, allowing multiple people to collaborate on projects.

If you are interested in learning more about Git, please visit the [official Git documentation](https://git-scm.com/doc). For GitHub-specific features, visit the [GitHub Docs](https://docs.github.com).

## Is This Guide For You?

This guide is for beginner developers and CST students who can write code but have not used Git or GitHub before. We will walk you through the most common Git operations in a Windows environment and provide a solid foundation for your future projects and collaboration with others.

By the end of this guide, you will know how to:

- **[Clone a Repository](cloning.md)** - Download an existing GitHub repository to your local machine.
- **[Commit and Push Changes](committing-and-pushing.md)** - Save your work locally and upload it to GitHub.
- **[Branch and Merge](branching-and-merging.md)** - Work on features in isolation and combine them back into the main codebase.
- **[Resolve Merge Conflicts](resolving-merge-conflicts.md)** - Handle situations where two branches edit the same lines of code.

## Prerequisites

To follow these instructions, you will need:

- A computer with **Windows 11** operating system
- A [**GitHub account**](https://github.com/join)
- Ability to open the [**VS Code terminal**](https://code.visualstudio.com/docs/terminal/basics) and type commands such as `cd` to navigate between folders
- An active internet connection

## Software Requirements

Before proceeding, ensure you have the following installed:

- [**Git**](https://git-scm.com/downloads) version 2.51 or later, configured with your name and email
- [**Visual Studio Code**](https://code.visualstudio.com/download) version 1.112 or later
- A modern web browser such as Chrome version 145 or later, Firefox version 148 or later, or Edge version 146 or later

> Although the screenshots provided will be from VS Code, most of the instructions can be followed using any terminal application.
> Alternatives such as [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701), [Git Bash](https://gitforwindows.org/), and [PowerShell](https://learn.microsoft.com/en-us/powershell/) are also viable options.


## Typographical Conventions

This guide uses the following formatting conventions throughout:

1. Commands, file names, branch names, and terminal output are displayed in `inline code` formatting:

    Use `git add .` to stage all changes, then check the file `index.html` on the `main` branch.

2. Actions you need to perform, button names, and menu items are **bolded**:

    **Click** the green **<> Code** button, then select **HTTPS**.

3. Multi-line commands and terminal output are shown in fenced code blocks with syntax highlighting:

    ```bash
    git add .
    git commit -m "Your message here"
    git push
    ```

4. Instructions that require you to run a command in the terminal will be formatted like:

    ```
    run some command in the terminal
    ```

## Admonitions

Throughout the documentation, we will use message blocks to alert you to relevant information. Each possible message block, from most important to least important:

!!! danger "Danger"
    This is what we will use to warn you about actions that may cause errors, data loss, or unexpected behavior.

!!! info "Notes"
    This is what we will use to indicate if we may have any side notes that may be useful.

!!! success "Success"
    This is what it looks like if you did something correct.