# Task 3: Branching and Merging

## Overview

So far, you have been working directly on the **main** branch. This works fine for solo projects, but in real-world development, you will want to work on new features or fixes without risking the stability of your main codebase. This is where **branches** come in.

A branch is an independent line of development. You can create a branch, make changes on it, and then **merge** it back into `main` when your work is complete and tested.

By the end of this task, you will be able to:

- Create a new branch
- Switch between branches
- Make commits on a feature branch
- Pull the latest changes from the remote repository
- Merge a branch into `main`
- Delete a branch after merging

---

## Creating a New Branch

Before making changes, create a new branch for your work. Branch names should be short and descriptive of what you are working on.

1. **Run** the following command to create and switch to a new branch:

    ```bash
    git checkout -b feature/add-contact-page
    ```

    This command does two things at once: it **creates** a new branch called `feature/add-contact-page` and **switches** you to that branch immediately.

You should see:

```
Switched to a new branch 'feature/add-contact-page'
```

![Screenshot of terminal showing branch creation](images/task3-create-branch.png "Creating a new branch with git checkout -b"){: alt="Terminal window displaying the output of git checkout -b showing a new branch was created and switched to"}

*Figure 1: Creating and switching to a new branch.*

!!! info "Branch Naming Conventions"
    Good branch names describe what you are working on. Common prefixes include:

    - `feature/` - for new features (e.g., `feature/add-login-page`)
    - `bugfix/` - for bug fixes (e.g., `bugfix/fix-nav-links`)
    - `hotfix/` - for urgent fixes (e.g., `hotfix/security-patch`)

    Avoid spaces in branch names. Use hyphens (`-`) or slashes (`/`) instead.

---

## Verifying Your Current Branch

To confirm which branch you are on, check the branch list.

1. **Run** the following command:

    ```bash
    git branch
    ```

You should see a list of branches with an asterisk (`*`) next to the active one:

```
  main
* feature/add-contact-page
```

![Screenshot of git branch output](images/task3-git-branch.png "git branch output showing the active branch"){: alt="Terminal window displaying git branch output with an asterisk next to the currently active feature branch"}

*Figure 2: The branch list with the active branch highlighted.*

!!! success "Success"
    If you see the asterisk next to your new branch name, you are on the correct branch and ready to start making changes.

!!! info "Switching Between Branches"
    To switch back to `main` (or any other branch) at any time, run:

    ```bash
    git checkout main
    ```

    Make sure you commit or stash your changes before switching branches, otherwise Git may not let you switch.

---

## Making Changes on Your Branch

Now you can work on your feature. Any changes you commit here will only exist on this branch and will not affect `main`.

1. **Create** or modify files for your feature (e.g., create a `contact.html` file).
2. **Stage** your changes:

    ```bash
    git add .
    ```

3. **Commit** your changes:

    ```bash
    git commit -m "Add contact page with form and map"
    ```

You can make multiple commits on your branch as you work. Each commit captures a step in your progress.

![Screenshot of making a commit on the feature branch](images/task3-commit-on-branch.png "Committing changes on a feature branch"){: alt="Terminal window showing git add and git commit commands being run on a feature branch"}

*Figure 3: Committing changes on the feature branch.*

---

## Pulling the Latest Changes from Main

Before merging your branch into `main`, it is important to make sure your local `main` branch is up to date with the remote repository. This is especially important when working with a team, as others may have pushed changes while you were working.

1. **Switch** back to the `main` branch:

    ```bash
    git checkout main
    ```

2. **Pull** the latest changes from GitHub:

    ```bash
    git pull
    ```

You should see output like:

```
Already up to date.
```

Or, if there are new changes:

```
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
Updating c3d4e5f..f6g7h8i
Fast-forward
 index.html | 10 +++++-----
 1 file changed, 5 insertions(+), 5 deletions(-)
```

![Screenshot of git pull output](images/task3-git-pull.png "Pulling latest changes with git pull"){: alt="Terminal window displaying the output of git pull showing the repository is up to date"}

*Figure 4: Pulling the latest changes from the remote repository.*

!!! danger "Don't Skip This Step"
    If you skip pulling before merging, you risk creating **merge conflicts** (covered in Task 4). Always pull the latest changes from `main` before merging your feature branch.

---

## Merging Your Branch into Main

Now that `main` is up to date, you can merge your feature branch into it.

1. **Ensure** you are on the `main` branch (the branch you want to merge **into**):

    ```bash
    git checkout main
    ```

2. **Run** the merge command:

    ```bash
    git merge feature/add-contact-page
    ```

You should see output like:

```
Updating f6g7h8i..j9k0l1m
Fast-forward
 contact.html | 30 ++++++++++++++++++++++++++++++
 1 file changed, 30 insertions(+)
 create mode 100644 contact.html
```

![Screenshot of git merge output](images/task3-merge-output.png "Merging a feature branch into main"){: alt="Terminal window displaying the output of git merge showing a successful fast-forward merge"}

*Figure 5: A successful merge of the feature branch into main.*

!!! success "Success"
    If the merge completes without errors, your feature branch changes are now part of `main`!

!!! info "What is Fast-Forward?"
    A **fast-forward** merge happens when `main` has not changed since you created your branch. Git simply moves the `main` pointer forward to include your new commits. If `main` has changed, Git will create a **merge commit** instead, which combines the histories of both branches.

---

## Pushing the Merged Changes

After merging locally, push the updated `main` branch to GitHub.

1. **Run** the following command:

    ```bash
    git push
    ```

![Screenshot of pushing the merged changes](images/task3-push-merged.png "Pushing merged changes to GitHub"){: alt="Terminal window displaying the output of git push after merging a feature branch"}

*Figure 6: Pushing the merged changes to GitHub.*

---

## Deleting the Feature Branch

Once your feature branch has been merged, you no longer need it. Cleaning up old branches keeps your repository organized.

1. **Delete** the local branch:

    ```bash
    git branch -d feature/add-contact-page
    ```

    You should see:

    ```
    Deleted branch feature/add-contact-page (was j9k0l1m).
    ```

2. **Delete** the remote branch (if you pushed it to GitHub earlier):

    ```bash
    git push origin --delete feature/add-contact-page
    ```

!!! info "Why Delete Branches?"
    Over time, old branches pile up and make it harder to see what is actively being worked on. Deleting merged branches is a common housekeeping practice in professional development.

!!! danger "Don't Use `-D` Unless You Mean It"
    The uppercase `-D` flag (`git branch -D branch-name`) force-deletes a branch even if it has not been merged. Only use this if you are absolutely sure you want to discard the work on that branch.

---

## Conclusion

In this task, you learned how to:

- Create a new branch with `git checkout -b`
- Verify and switch between branches with `git branch` and `git checkout`
- Make commits on a feature branch
- Pull the latest changes from the remote with `git pull`
- Merge a branch into `main` with `git merge`
- Delete branches after merging with `git branch -d`

Branching lets you work on features, fixes, and experiments without risking the stability of your main codebase. In the next task, you will learn how to handle **merge conflicts**, which is what happens when two branches change the same lines of code.
