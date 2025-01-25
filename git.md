# Git Cheat Sheet

## What is Git?
Git is a version control system that tracks changes in a project, including who made the changes, where, and when. It’s essential for version control and collaboration in software development.

## What is GitHub?
GitHub is an online platform for hosting and managing Git repositories.

### Download Git:
[Download Git](https://git-scm.com/downloads)

---

## Basic Terminal Commands

| **Command**     | **Description**                                   |
|------------------|-------------------------------------------------|
| `ls`            | List all files in the current directory          |
| `pwd`           | Show the current directory path                 |
| `mkdir`         | Create a new directory                          |
| `cd`            | Navigate to a specific directory                |
| `ls -a`         | List all files, including hidden ones           |
| `touch`         | Create a new file                               |
| `vi`            | Open a file in the Vim editor                  |
| `nano`          | Open a file in the Nano editor                 |
| `cat`           | Display the contents of a file                 |
| `ctrl + o`      | Save changes in the editor                     |
| `ctrl + x`      | Exit the editor                                |
| `rm -rf`        | Delete a file or directory                     |

---

## Essential Git Commands

### 1. `git init`
- Initializes a new Git repository by creating a hidden `.git` folder to track project changes.
- View hidden files using `ls -a`.

The `.git` folder contains important components like:
- `branches`
- `config`
- `description`
- `HEAD`
- `hooks`
- `info`
- `objects`
- `refs`

### 2. `git status`
- Displays the repository’s status, including:
  - Untracked files
  - Changes since the last commit

#### Analogy:
Creating a wedding photo album:
1. **Untracked files**: Guests without photos.
2. **Staging**: Calling guests to the stage (`git add .`).
3. **Committing**: Capturing and saving the photo (`git commit -m "message"`).

### 3. `git add .`
- Stages all untracked files for the next commit.
- To stage specific files or folders:
  ```bash
  git add <file_name>
  ```
- Staged files appear in green under *"Changes to be committed"* when you run `git status`.

### 4. Unstaging Files
- **`git rm --cached <file>`**: Stops tracking a file entirely.
- **`git restore --staged <file>`**: Unstages a file but keeps tracking its changes.

#### Use Case:
Accidentally staged large files (e.g., `venv`)? Unstage them with:
```bash
git rm --cached <file_name>
```

### 5. `git commit -m "message"`
- Saves a snapshot of changes with a descriptive message.
- Example:
  ```bash
  git commit -m "learning"
  [master e70f50e] learning
   1 file changed, 1 insertion(+)
   create mode 100644 test.txt
  ```

### 6. `git log`
- Displays the commit history with details like:
  - Commit ID
  - Author
  - Date and time

#### Example:
```bash
git log
commit e70f50e44780995fb73413dab530d9c91e0debec (HEAD -> master)  
Author: AbhinavSarkarr <abhinav.sarkar@jellyfishtechnologies.com>
Date:   Fri Jan 24 20:21:37 2025 +0530

    learning
```

### 7. `git reset`
- Reverts commits and undoes changes.

#### Types of `git reset`:
1. **`git reset --soft HEAD~`**: Uncommits the last commit but keeps changes staged.
2. **`git reset HEAD~`**: Uncommits the last commit and unstages changes.
3. **`git reset --hard HEAD~`**: Uncommits, unstages, and deletes all changes.

#### Go Back to a Specific Commit:
```bash
git reset <commit_log>
```

### 8. `git stash`
- Temporarily saves uncommitted changes without committing them.
- Use this to revert to the last commit while preserving your changes.

#### Steps:
1. Stage changes with `git add`.
2. Run `git stash`.

*Your changes are saved in the stash and removed from your code.*

### 9. `git stash pop`
- Restores stashed changes to your code.
- Combines the stashed changes with any new changes made after stashing.

### 10. `git stash clear`
- Permanently removes all stashed changes.

---

## Q&A

**Q: What happens if I stage new changes after using `git stash`, then run `git stash pop`?**
- A: The new changes remain, and the stashed changes are combined with them.

