---
tags: ["git","github","colloaboration"]
date: 2026-03-18T10:00:00+05:00
publishDate: 2026-03-18T00:00:00+05:00
draft: false

---

# Git and GitHub: Basic Commands Guide

## Introduction

Git is a distributed version control system used to track changes in code. GitHub is a platform that hosts Git repositories and enables collaboration.

---

## 1. Setting Up Git

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

Check configuration:

```bash
git config --list
```

---

## 2. Creating a Repository

Initialize a new repository:

```bash
git init
```

Clone an existing repository:

```bash
git clone https://github.com/username/repo.git
```

---

## 3. Basic Workflow

### Check Status

```bash
git status
```

### Add Files

Add a single file:

```bash
git add filename
```

Add all files:

```bash
git add .
```

### Commit Changes

```bash
git commit -m "Your commit message"
```

---

## 4. Branching

Create a branch:

```bash
git branch branch_name
```

Switch to a branch:

```bash
git checkout branch_name
```

Create and switch in one command:

```bash
git checkout -b branch_name
```

List branches:

```bash
git branch
```

---

## 5. Merging

Merge a branch into current branch:

```bash
git merge branch_name
```

---

## 6. Working with Remote (GitHub)

Add remote repository:

```bash
git remote add origin https://github.com/username/repo.git
```

Push code:

```bash
git push origin main
```

Pull latest changes:

```bash
git pull origin main
```

Fetch updates:

```bash
git fetch
```

---

## 7. Viewing History

```bash
git log
```

Compact view:

```bash
git log --oneline
```

---

## 8. Undoing Changes

Unstage a file:

```bash
git reset filename
```

Discard changes:

```bash
git checkout -- filename
```

Reset last commit:

```bash
git reset --soft HEAD~1
```

---

## 9. .gitignore File

Used to ignore files/folders:

```
node_modules/
.env
*.log
```

---

## 10. Typical Workflow Example

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/username/repo.git
git push -u origin main
```

---

## Conclusion

Git and GitHub are essential tools for developers. Mastering these basic commands helps you manage projects efficiently and collaborate with others.
