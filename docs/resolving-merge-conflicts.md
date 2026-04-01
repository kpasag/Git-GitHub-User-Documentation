# Task 4: Resolving Merge Conflicts

## Overview

Merge conflicts happen when two branches modify the **same lines** in the same file. Git does not know which version to keep, so it asks you to resolve the conflict manually. This is completely normal and happens regularly in team projects.

While merge conflicts can seem intimidating at first, they are straightforward to fix once you understand the process.

By the end of this task, you will be able to:

- Understand why merge conflicts occur
- Identify conflict markers in a file
- Resolve a merge conflict using VS Code
- Complete the merge after resolving conflicts

---

## Understanding How Conflicts Happen

A merge conflict occurs when:

1. You create a branch from `main` and edit a file (e.g., line 5 of `index.html`).
2. Someone else (or you, on another branch) also edits **the same line** on `main`.
3. When you try to merge your branch into `main`, Git finds two different versions of the same line and does not know which one to keep.

!!! info "When Conflicts Don't Happen"
    If two branches edit **different files**, or **different lines** in the same file, Git can merge them automatically without any conflict. Conflicts only happen when the exact same lines are changed in both branches.

---

## Creating a Conflict (For Practice)

To practice resolving a conflict, let's intentionally create one.

### Making a Change on Main

1. **Ensure** you are on the `main` branch:

    ```bash
    git checkout main
    ```

2. **Open** `index.html` (or any file in the project) and change the `<h1>` tag on line 1 to:

    ```html
    <h1>Welcome to My Website</h1>
    ```

3. **Stage** and **commit** the change:

    ```bash
    git add index.html
    git commit -m "Update heading on main"
    ```

### Making a Conflicting Change on a Feature Branch

1. **Create** and switch to a new branch:

    ```bash
    git checkout -b feature/update-heading
    ```

2. **Reset** the branch back one commit so it does not have the change you just made on `main`:

    ```bash
    git reset HEAD~1 --hard
    ```

    !!! danger "Important"
        This step is necessary for the exercise to create a conflict. The `git reset --hard` command will discard changes, so only use it when you are sure you want to go back.

3. **Edit** the **same line** in `index.html` with a different heading:

    ```html
    <h1>Welcome to Our Amazing Website</h1>
    ```

4. **Stage** and **commit** the change:

    ```bash
    git add index.html
    git commit -m "Update heading on feature branch"
    ```

### Triggering the Conflict

1. **Switch** back to `main`:

    ```bash
    git checkout main
    ```

2. **Run** the merge command:

    ```bash
    git merge feature/update-heading
    ```

You should see:

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

![Screenshot of merge conflict message in terminal](images/task4-conflict-message.png "Merge conflict message in terminal"){: alt="Terminal window displaying the output of git merge showing a merge conflict in index.html"}

*Figure 1: The merge conflict message in the terminal.*

!!! success "Success"
    If you see the `CONFLICT` message, you have successfully triggered a merge conflict. This is expected, so do not panic!

---

## Identifying the Conflict Markers

When a conflict occurs, Git inserts special markers into the conflicted file to show you both versions.

1. **Open** the conflicted file (`index.html`) in VS Code.

You will see something like this:

```
<<<<<<< HEAD
<h1>Welcome to My Website</h1>
=======
<h1>Welcome to Our Amazing Website</h1>
>>>>>>> feature/update-heading
```

![Screenshot of conflict markers in VS Code](images/task4-conflict-markers.png "Conflict markers shown in VS Code"){: alt="VS Code editor showing a file with conflict markers including the HEAD version, separator, and incoming branch version"}

*Figure 2: Conflict markers in VS Code.*

Here is what each marker means:

| Marker | Meaning |
|--------|---------|
| `<<<<<<< HEAD` | The start of the **current branch's** version (in this case, `main`) |
| `=======` | The divider between the two versions |
| `>>>>>>> feature/update-heading` | The end of the **incoming branch's** version |

Everything between `<<<<<<< HEAD` and `=======` is what is currently on `main`. Everything between `=======` and `>>>>>>> feature/update-heading` is what is on the feature branch.

!!! info "VS Code Highlighting"
    VS Code will highlight conflicts with color-coded blocks and show buttons above the conflict:

    - **Accept Current Change** - keeps the `main` version
    - **Accept Incoming Change** - keeps the feature branch version
    - **Accept Both Changes** - keeps both versions, one after the other
    - **Compare Changes** - opens a side-by-side diff view

![Screenshot of VS Code conflict resolution buttons](images/task4-vscode-buttons.png "VS Code merge conflict resolution buttons"){: alt="VS Code editor showing the color-coded conflict highlighting with Accept Current Change, Accept Incoming Change, Accept Both Changes, and Compare Changes buttons"}

*Figure 3: VS Code's built-in conflict resolution buttons.*

---

## Resolving the Conflict

You have three options for resolving the conflict:

### Option A: Accept One Version

1. **Click** **Accept Current Change** or **Accept Incoming Change** in VS Code to keep one version and discard the other.

### Option B: Accept Both

1. **Click** **Accept Both Changes** to keep both lines. This is useful when both changes are needed.

### Option C: Edit Manually

1. **Delete** the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) from the file.
2. **Write** the final version yourself. For example:

    ```html
    <h1>Welcome to Our Website</h1>
    ```

3. **Save** the file.

![Screenshot of resolved conflict in VS Code](images/task4-resolved-conflict.png "Resolved merge conflict in VS Code"){: alt="VS Code editor showing the file after the conflict has been resolved with conflict markers removed and final content in place"}

*Figure 4: The file after resolving the conflict.*

!!! danger "Remove ALL Conflict Markers"
    If you choose to edit manually, make sure you delete **all** of the conflict markers. Leaving them in will break your code. Your file should look like a normal file with no `<<<<<<<`, `=======`, or `>>>>>>>` characters anywhere.

---

## Completing the Merge

After resolving the conflict, you need to tell Git that the conflict is fixed.

1. **Save** the file in VS Code.
2. **Stage** the resolved file:

    ```bash
    git add index.html
    ```

3. **Commit** the merge:

    ```bash
    git commit -m "Resolve merge conflict in index.html heading"
    ```

4. **Push** the resolved merge to GitHub:

    ```bash
    git push
    ```

![Screenshot of terminal showing the completed merge commit and push](images/task4-merge-complete.png "Completed merge conflict resolution"){: alt="Terminal window showing git add, git commit, and git push commands completing a merge conflict resolution"}

*Figure 5: Completing the merge after resolving the conflict.*

!!! success "Success"
    If your push succeeds and the file looks correct on GitHub, you have successfully resolved a merge conflict!

---

## Verifying on GitHub

As a final check, confirm your resolution appears correctly on GitHub.

1. **Open** your repository on [github.com](https://github.com).
2. **Check** that the merge commit appears in the commit history.
3. **Click** on the resolved file to confirm it contains your final version.
4. **Verify** that no conflict markers are left in any files.

![Screenshot of GitHub showing the merge commit](images/task4-github-resolved.png "GitHub repository showing the merge commit"){: alt="GitHub repository page with the merge conflict resolution commit visible in the commit history"}

*Figure 6: The merge commit visible on GitHub.*

---

## Conclusion

In this task, you learned how to:

- Understand why merge conflicts happen
- Read and interpret conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
- Resolve conflicts using VS Code's built-in tools or by editing manually
- Complete a merge after resolving conflicts with `git add`, `git commit`, and `git push`

Merge conflicts are a normal part of working with Git, especially in teams. The more you practice, the less intimidating they become. You now have all the core Git skills you need to clone, commit, branch, merge, and resolve conflicts!
