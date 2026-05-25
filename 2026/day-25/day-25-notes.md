# Day 25 – Git Reset vs Revert & Branching Strategies

## Task 1: Git Reset

### Difference between --soft, --mixed, and --hard

#### git reset --soft
Moves HEAD backward but keeps changes staged.

#### git reset --mixed
Moves HEAD backward and keeps changes unstaged.

#### git reset --hard
Moves HEAD backward and removes commits and changes completely.

### Which one is destructive and why?

git reset --hard is destructive because it permanently removes commits and file changes from the working directory.

### When would you use each one?

- --soft → to change a commit message or recommit quickly
- --mixed → to unstage changes and edit before recommitting
- --hard → to completely discard unwanted local changes

### Should you ever use git reset on commits that are already pushed?

No, because reset rewrites commit history and can create issues for collaborators.

### Observation

Performed `--soft`, `--mixed`, and `--hard` reset using `HEAD~1` and observed differences in staging and file changes.

---

## Task 2: Git Revert

### How is git revert different from git reset?

git revert creates a new commit to undo changes, while git reset removes commits from history.

### Why is revert considered safer than reset for shared branches?

Revert preserves commit history and safely undoes changes without rewriting history.

### When would you use revert vs reset?

- `git revert` → shared or pushed branches
- `git reset` → local commits before pushing

### Why didn’t we use git commit after git add during revert conflict?

When a revert conflict occurs, Git pauses an already ongoing revert commit. After resolving the conflict and staging the file with `git add`, we use `git revert --continue` to continue and finish the same revert process instead of creating a new commit manually.

### Observation

Reverted the middle commit and resolved the revert conflict manually using `git revert --continue`.

---

## Task 3: Reset vs Revert Summary

| Feature | git reset | git revert |
|----------|------------|-------------|
| What it does | Moves HEAD backward and removes commits | Creates a new commit to undo changes |
| Removes commit from history? | Yes | No |
| Safe for shared/pushed branches? | No | Yes |
| When to use | Local commits, fixing mistakes before push | Shared branches or safely undoing pushed commits |

---

## Task 4: Branching Strategies

### 1. GitFlow

#### How it works

GitFlow uses multiple branches such as `main`, `develop`, `feature`, `release`, and `hotfix` branches.

#### Flow

- `main` → production code
- `develop` → development branch
- `feature/*` → new features
- `release/*` → release preparation
- `hotfix/*` → urgent production fixes

Text Diagram:

```text
main
 ↑
release
 ↑
develop
↙     ↘
feature  feature
```

#### Used in

Large teams and projects with scheduled releases.

#### Pros

- Organized workflow
- Better release management
- Good for large teams

#### Cons

- Complex
- Too many branches
- Slower development

---

### 2. GitHub Flow

#### How it works

Developers create short-lived feature branches from `main` and merge back through pull requests.

Text Diagram:

```text
main
 ├── feature-login
 ├── feature-payment
 └── feature-profile
```

#### Used in

Startups, SaaS products, and fast-moving teams.

#### Pros

- Simple
- Fast deployments
- Easy collaboration

#### Cons

- Less structured
- Can become messy in large teams

---

### 3. Trunk-Based Development

#### How it works

Developers frequently merge small changes directly into the `main` branch using short-lived branches.

Text Diagram:

```text
main
 ↑ ↑ ↑ ↑
small frequent commits
```

#### Used in

CI/CD environments and large tech companies.

#### Pros

- Faster integration
- Fewer merge conflicts
- Great for CI/CD

#### Cons

- Requires strong automated testing
- Risky without proper testing

---

## Answers

### Which strategy would you use for a startup shipping fast?

GitHub Flow because it is simple and supports fast deployment.

### Which strategy would you use for a large team with scheduled releases?

GitFlow because it provides structured release management.

### Which one does your favorite open-source project use?

Kubernetes uses a GitHub-based workflow with pull requests and branch management.
