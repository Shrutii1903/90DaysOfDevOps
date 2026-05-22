# Day 23 – Git Branching & GitHub Basics


---

## 🌿 Key Concepts Learned

### 1. Branching in Git
Branches allow us to work on different features or fixes independently without affecting the main codebase.

- `main/master` → stable production code
- feature branches → experimental or new work

---

### 2. HEAD in Git
HEAD points to the current branch/commit we are working on.

---

### 3. Working Directory vs Staging vs Repository

- **Working Directory** → where we edit files
- **Staging Area** → where changes are prepared (`git add`)
- **Repository** → where commits are stored (`git commit`)

---

### 4. Git Commands Practiced

- `git branch` → list branches
- `git branch <name>` → create branch
- `git switch <name>` → switch branch
- `git checkout -b <name>` → create + switch branch
- `git add .` → stage changes
- `git commit -m ""` → save changes
- `git log --oneline` → view commit history
- `git push origin <branch>` → push to GitHub
- `git pull origin <branch>` → fetch + merge changes

---

## 🌐 GitHub Concepts

### Origin vs Upstream

- **origin** → your remote repository (GitHub repo)
- **upstream** → original repository (used in forks)

---

### Fetch vs Pull

- `git fetch` → downloads changes only
- `git pull` → downloads + merges changes

---

### Clone vs Fork

- **Clone** → copy repo to local machine using Git
- **Fork** → copy repo to your GitHub account

---

## 🔄 Branching Practice

- Created multiple branches (`feature-1`, `feature-2`)
- Switched between branches
- Made commits in isolated branches
- Deleted unnecessary branches
- Verified commit isolation between branches

---

## ☁️ GitHub Integration

- Connected local repo to GitHub using `origin`
- Pushed multiple branches to GitHub
- Pulled changes from GitHub to local system
- Verified SSH authentication setup

---

## 🔐 SSH Setup

- Generated SSH key pair
- Added public key to GitHub
- Configured ssh-agent
- Successfully authenticated GitHub without password

---

## 🧠 Key Takeaways

- Branching is essential for parallel development
- Git staging area gives control over commits
- Remote repositories enable collaboration
- SSH is the preferred secure authentication method in DevOps
- Git workflows mirror real-world team development processes

---



---
