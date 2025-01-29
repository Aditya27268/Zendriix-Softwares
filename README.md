# Git Workflow Architecture for Monthly Releases

## Overview
This repository demonstrates a **Git Workflow Architecture** to manage **product releases on the 25th of every month** at Zendriix Softwares. The workflow ensures a structured branching strategy for **feature development, testing, and deployment.**

---

## **Git Workflow Structure**

### **Branches Used:**
1. **`main`** (Production branch) - Contains the stable release versions.
2. **`develop`** (Development branch) - Integrates feature branches before release.
3. **`release`** (Pre-production branch) - Created on the **15th of each month** for testing.
4. **`feature/*`** (Feature branches) - Used for new feature development.

### **Workflow Timeline:**
- **1st – 14th:** Feature development in `feature/*` branches → Merge into `develop`.
- **15th:** Create a `release` branch from `develop` → Begin testing.
- **15th – 24th:** QA and bug fixes happen on the `release` branch.
- **25th:** Merge `release` into `main` → Tag the new release.
- **Post 25th:** Merge `main` back into `develop` for the next cycle.

---

## **Step-by-Step Implementation**

### **Step 1: Initialize the Repository**
```bash
mkdir git-workflow-simulation
cd git-workflow-simulation
git init
git branch -M master
```

### **Step 2: Create and Manage Branches**
```bash
git checkout -b develop
git checkout -b feature/login-module
git checkout -b feature/payment-gateway
```
After finishing the features, merge them into `develop`:
```bash
git checkout develop
git merge feature/login-module
git merge feature/payment-gateway
git branch -d feature/login-module
git branch -d feature/payment-gateway
```

### **Step 3: Create a Release Branch (15th of the Month)**
```bash
git checkout -b release-v1.0 develop
```
QA and bug fixes happen here.

After testing, merge into `main`:
```bash
git checkout main
git merge release-v1.0
git tag -a v1.0 -m "Release version 1.0"
```

### **Step 4: Merge `main` Back into `develop` (Post-Release)**
```bash
git checkout develop
git merge main
```

## **Conclusion**
This Git Workflow ensures **structured development, stable releases, and efficient bug fixing**. The workflow repeats monthly for continuous improvements and releases.

---


