# Git & GitHub 

---

## 1. Introduction to Git & GitHub

### What is Git?

* Git is a **Version Control System (VCS)**.
* It helps track changes in files over time.
* It allows us to go back to previous versions if something breaks.
* Git works **locally** on your computer.

**Simple example:**

> Git is like the *history feature in Google Docs* for your code.

---

### What is GitHub?

* GitHub is a **cloud platform** that stores Git repositories.
* It helps developers **share, collaborate, and back up code**.
* GitHub works **online**, Git works **offline**.

---

### Git vs GitHub

| Git            | GitHub              |
| -------------- | ------------------- |
| Tool           | Platform            |
| Works locally  | Works on cloud      |
| Tracks changes | Stores repositories |

---

## 2. Git Repository & git init

### What is a Repository?

* A repository (repo) is a **project folder tracked by Git**.
* It contains files, folders, and Git history.

---

### git init

* `git init` initializes Git in a folder.
* It creates a hidden `.git` folder.
* Without `git init`, Git commands will not work.

**Command:**

```
git init
```

**Important rule:**

> You must run `git init` before using `git add` or `git commit`.

---

## 3. Git Configuration

### Why Git Config is Needed?

* Git needs to know **who is making the changes**.
* Name and email are attached to every commit.

---

### Check Configuration

```
git config --list
git config user.name
git config user.email
```

---

### Set or Change Email

**Global (all projects):**

```
git config --global user.email "email@example.com"
```

**Local (current project only):**

```
git config --local user.email "email@example.com"
```

**Note:**

* Local config overrides global config.
* Config changes apply only to **future commits**.

---

## 4. Git Areas (Very Important Concept)

Git has **three main areas**:

### 1. Working Directory

* Where you create and edit files.
* Git sees changes but does not save them yet.

### 2. Staging Area

* Temporary area where selected changes are kept.
* Used to decide **what will go into the next commit**.

### 3. Repository (Commit History)

* Permanent saved snapshots of your project.

**Flow:**

```
Working Directory → Staging Area → Repository
```

---

## 5. Basic Git Commands

### Check Status

```
git status
```

Shows:

* Untracked files
* Staged files
* Modified files

---

### Add Files to Staging

```
git add file.txt
git add .
```

**Note:**

> `git add` does NOT save the file. It only prepares it.

---

### Commit Changes

```
git commit -m "Commit message"
```

* Commit = permanent save point
* Message should explain **what was done**

---

### View Commit History

```
git log
git log --oneline
```

If `(END)` appears:

* Press `q` to exit

---

## 6. Branches in Git

### What is a Branch?

* A branch is a **separate line of development**.
* Used to work safely without affecting main code.

**Main branch:** Production-ready code

---

### Create Branch

```
git branch branch-name
```

### Switch Branch

```
git checkout branch-name
git switch branch-name
```

### Merge Branch

```
git checkout main
git merge branch-name
```

---

### Delete Branch

**Safe delete (merged branch):**

```
git branch -d branch-name
```

**Force delete (dangerous):**

```
git branch -D branch-name
```

**Remote branch delete:**

```
git push origin --delete branch-name
```

---

## 7. Git Merge Editor (Vim Screen)

* Git opens an editor to confirm merge commit message.
* This is NOT an error.

**To save and exit:**

```
Esc → :wq → Enter
```

**To exit without saving:**

```
Esc → :q!
```

---

## 8. GitHub Integration

### Clone Repository

```
git clone <repo-url>
```

---

### Connect Local Repo to GitHub

```
git remote add origin <repo-url>
```

Verify:

```
git remote -v
```

---

### Push Code to GitHub

```
git push -u origin main
```

---

### Pull Latest Code

```
git pull origin main
```

---

## 9. master vs main Branch Issue

### Why It Happens?

* Older Git → `master`
* GitHub standard → `main`

### Fix (Recommended)

```
git branch -M main
git push -u origin main
```

---

## 10. Undoing Changes

### Git Revert

* Creates a new commit that undoes changes
* Safe for shared branches

```
git revert <commit-id>
```

---

### Git Reset

**Soft reset:**

```
git reset --soft HEAD~1
```

**Mixed reset:**

```
git reset HEAD~1
```

**Hard reset (dangerous):**

```
git reset --hard HEAD~1
```

---

## 11. Git Amend

Used to modify the **last commit**.

**Change commit message:**

```
git commit --amend -m "New message"
```

**Add changes to last commit:**

```
git add .
git commit --amend
```

---

## 12. Key Rules to Remember

* `git init` is mandatory
* `git add` ≠ save
* `git commit` ≠ push to GitHub
* Always check `git status`
* Use branches for safety
* Be careful with `reset --hard`

---

## 13. Common Interview Questions (Quick Prep)

* What is Git?
* What is staging area?
* Difference between Git and GitHub
* Difference between revert and reset
* What is a branch?
* What is git commit?

---
