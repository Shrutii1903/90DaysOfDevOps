# Day 26 – GitHub CLI: Manage GitHub from Your Terminal

## What is GitHub CLI?

GitHub CLI (`gh`) is a command-line tool that allows us to manage GitHub directly from the terminal without opening the browser.

It helps in:
- Creating repositories
- Managing pull requests
- Creating and tracking issues
- Working with GitHub Actions
- Automating GitHub workflows

---

## Task 1: Install and Authenticate

### Commands Used

```bash
sudo apt install gh -y
gh --version
gh auth login
gh auth status
```

### Observation

Installed GitHub CLI and authenticated GitHub account successfully using browser login.

Verified active account and authentication status.

### What authentication methods does `gh` support?

- Browser-based authentication
- Personal Access Token (PAT)
- SSH authentication

---

## Task 2: Working with Repositories

### Commands Used

```bash
gh repo create gh-test-repo --public --clone --add-readme
gh repo clone Shrutii1903/gh-test-repo gh-clone-test
gh repo view
gh repo list Shrutii1903
gh repo view --web
```

### Observation

Created a repository directly from terminal, cloned repository using GitHub CLI, viewed repository details, listed repositories, and opened repository in browser.

### Difference Between `git clone` and `gh repo clone`

| git clone | gh repo clone |
|------------|----------------|
| General Git command | GitHub CLI command |
| Requires repository URL | Uses `owner/repo` format |
| Works with any Git provider | GitHub-specific |
| No GitHub integration | Integrated with GitHub account |

---

## Task 3: Issues

### Commands Used

```bash
gh issue create
gh issue list
gh issue view 1
gh issue close 1
```

### Observation

Created an issue, viewed issue details, listed open issues, and closed issue directly from terminal.

### How could you use `gh issue` in automation?

`gh issue` can be used in scripts to automatically create issues for failed deployments, bugs, security alerts, or monitoring failures.

Example:
If CI/CD pipeline fails, automation can create a GitHub issue automatically.

---

## Task 4: Pull Requests

### Commands Used

```bash
git checkout -b feature-practice
git add .
git commit -m "updated readme for gh practice"
git push origin feature-practice

gh pr create --fill
gh pr list
gh pr view 2
gh pr merge 2
```

### Observation

Created a feature branch, pushed changes, created pull request, viewed PR details, and merged PR completely from terminal.

### What merge methods does `gh pr merge` support?

- Merge Commit
- Squash Merge
- Rebase Merge

### How would you review someone else's PR using `gh`?

We can review pull requests using:

```bash
gh pr view <pr-number>
gh pr checkout <pr-number>
```

This allows us to inspect code changes locally and review PR details from terminal.

---

## Task 5: GitHub Actions (Preview)

### Commands Used

```bash
gh run list --repo kubernetes/kubernetes
```

### Observation

Viewed GitHub Actions workflow runs and checked workflow status of a public repository.

### How could `gh run` and `gh workflow` help in CI/CD?

They help monitor CI/CD pipelines directly from terminal.

We can:
- Check workflow status
- Monitor failed jobs
- Debug pipeline failures
- Trigger workflows
- View logs without opening GitHub UI

---

## Task 6: Useful `gh` Commands

### Useful Commands Explored

```bash
gh api
gh gist
gh release
gh alias
gh search repos
```

### Examples

#### Search repositories

```bash
gh search repos devops
```

#### Create aliases

```bash
gh alias set co "pr checkout"
```

---

## Summary

Learned how to manage GitHub from terminal using GitHub CLI (`gh`), including repositories, issues, pull requests, and workflow monitoring.
