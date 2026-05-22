# Day 22 Notes – Introduction to Git

## 1. What is the difference between `git add` and `git commit`?

`git add` is used to move changes to the staging area. It prepares files for a commit.

`git commit` is used to save the staged changes permanently in Git history with a message.

Example:

```bash
git add .
git commit -m "Added Git notes"
```

---

## 2. What does the staging area do? Why doesn't Git just commit directly?

The staging area acts like a temporary checkpoint where changes are prepared before committing.

Git does not commit directly because developers may want to review, organize, or select only specific changes before saving them permanently.

This helps maintain a clean and meaningful commit history.

---

## 3. What information does `git log` show?

The `git log` command shows commit history, including:

- Commit ID (hash)
- Author name
- Date and time
- Commit message

Example:

```bash
git log
```

For a compact view:

```bash
git log --oneline
```

---

## 4. What is the `.git/` folder and what happens if you delete it?

The `.git/` folder is the hidden folder that stores all Git-related data, including:

- Commit history
- Branch information
- Configuration
- Repository metadata

If the `.git/` folder is deleted, the project will no longer be tracked as a Git repository, and all version history will be lost.

---

## 5. What is the difference between a working directory, staging area, and repository?

### Working Directory
The place where files are created and edited.

### Staging Area
A temporary area where selected changes are prepared before committing.

### Repository
The place where committed changes are permanently stored in Git history.

### Git Workflow

Working Directory → Staging Area → Repository 
thanks

Example:

```bash
git add .
git commit -m "Save changes"
```
