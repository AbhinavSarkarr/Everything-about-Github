```markdown
# Git Cheat Sheet

## What is Git?
Git is a version control system responsible for keeping a record of who made which change, in which part, and at what time of the project. Essentially, it is a tool for version control.

## What is GitHub?
GitHub is an online platform that allows hosting Git repositories.

### Download Git:
[Download Git](https://git-scm.com/downloads)

---

## Basic Terminal Commands

| **Command**     | **Description**                                                                                 |
|------------------|---------------------------------------------------------------------------------------------|
| `ls`            | List all files in the current directory                                                     |
| `pwd`           | Print the path to the current directory                                                     |
| `mkdir`         | Create a new directory in the current location                                              |
| `cd`            | Change directory to the specified folder                                                   |
| `ls -a`         | List all files, including hidden ones                                                      |
| `touch`         | Create a new file                                                                          |
| `vi`            | Open the file in the Vim editor                                                           |
| `nano`          | Open the file in the Nano editor                                                          |
| `cat`           | Display the contents of a file in read-only mode                                           |
| `ctrl + o`      | Save changes while editing                                                                |
| `ctrl + x`      | Exit the editor                                                                           |
| `rm -rf`        | Delete a file or folder                                                                   |

---

## Git Commands

### 1. `git init`
- Initializes a new Git repository.
- Creates a hidden `.git` folder to store project history.
- Use `ls -a` to view hidden files, including `.git`.

The `.git` folder contains:
- `branches`
- `config`
- `description`
- `HEAD`
- `hooks`
- `info`
- `objects`
- `refs`

*Once initialized, any project changes are tracked by Git.*

---

### 2. `git status`
- Displays the status of the repository:
  - Lists untracked files.
  - Shows changes from the last commit.
- Untracked files are files with no history of changes.

**Analogy**:  
Think of creating a wedding photo album:
1. Untracked files = Guests without photos.
2. Staging = Calling guests to the stage (`git add .`).
3. Committing = Clicking and saving the photo (`git commit -m "message"`).

---

### 3. `git add .`
- Stages all untracked files for the next commit.
- To stage specific files or folders, use:  
  ```bash
  git add <file_name>
  ```
- After staging, `git status` shows files in green with the tag *"Changes to be committed."*

---

### 4. `git rm --cached <file>` / `git restore --staged <file>`
- **`git rm --cached <file>`**: Stops tracking the file entirely (removes it from Git index). Future changes won't be tracked.  
- **`git restore --staged <file>`**: Unstages the file but keeps tracking its changes.

Use case:  
If you mistakenly add large files (e.g., `venv`) using `git add .`, unstage them with:  
```bash
git rm --cached <file_name>
```

---

### 5. `git commit -m "message"`
- Saves a snapshot of the changes.
- Example:
  ```bash
  jellyfish@abhinav:~/Desktop/github$ git commit -m "learning"
  [master e70f50e] learning
   1 file changed, 1 insertion(+)
   create mode 100644 test.txt
  ```

---

### 6. `git log`
- Displays the commit history.
- Shows:
  - Commit ID
  - Author
  - Date and time of the commit

Example:
```bash
jellyfish@abhinav:~/Desktop/github$ git log
commit e70f50e44780995fb73413dab530d9c91e0debec (HEAD -> master)  
Author: AbhinavSarkarr <abhinav.sarkar@jellyfishtechnologies.com>
Date:   Fri Jan 24 20:21:37 2025 +0530

    learning
```

---

### 7. `git reset`
- Reverts commits and can be used to undo changes.

**Types of `git reset`:**
1. `git reset --soft HEAD~`:  
   - Uncommits the last commit but keeps changes in the staging area.
2. `git reset HEAD~`:  
   - Uncommits the last commit and unstages changes (removes them from the staging area).
3. `git reset --hard HEAD~`:  
   - Uncommits, unstages, and removes all code changes.

**Go back to a specific commit:**
```bash
git reset <commit_log>
```

---

### 8. `git stash`
- Temporarily saves changes without committing them.
- Use this when you want to revert your code to the last commit but don't want to lose changes.
- **Steps:**
  1. Stage changes using `git add`.
  2. Run `git stash`.

*All changes will be removed from the code and saved in the stash.*

---

### 9. `git stash pop`
- Restores the stashed changes to your code.
- If you made additional changes after stashing, they will be combined with the stashed changes.

---

### 10. `git stash clear`
- Clears the stash, permanently removing all stashed changes.

---

## Q&A

**Q: What happens if I make other changes and stage them after using `git stash`, then use `git stash pop`?**  
A: The new changes will remain, and the stashed changes will be combined with them.

```
