# ✅ HTML CI with GitHub Actions

This guide explains how to set up a **Continuous Integration (CI)** pipeline for a simple HTML project using **GitHub Actions**. The workflow will lint all HTML files using `htmlhint` whenever code is pushed to the `main` branch or a pull request is opened.

---

## 📁 Step 1: Create the Workflow File

Create the following path and file inside your project:

.github/workflows/html-ci.yml


---

## ✏️ Step 2: Add the Workflow Content

Paste the following into `html-ci.yml`:

```yaml
name: HTML CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  workflow_dispatch:  # Allows manual triggering

jobs:
  lint-html:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '20'

    - name: Install htmlhint
      run: npm install -g htmlhint

    - name: Run htmlhint on all HTML files
      run: htmlhint "**/*.html"

---

## 🚀 Step 3: Commit and Push the Workflow

After saving the file, commit and push it to your repository:

git add .github/workflows/html-ci.yml
git commit -m "Add HTML CI workflow"
git push origin main

---

## 🔁 Step 4: Trigger the Workflow
You can trigger the CI workflow in two ways:


## ✅ Automatic Trigger
Push any changes to the main branch.

Open a pull request targeting the main branch.

## 🖐️ Manual Trigger
Go to your GitHub repo → Actions tab.

Select HTML CI.

Click the "Run workflow" button (available because of workflow_dispatch).

---

## 📊 Step 5: Monitor the Workflow

Go to the Actions tab on GitHub.

Click on the latest run under HTML CI.

You’ll see step-by-step logs:

Code checkout

Node.js setup

htmlhint installation

HTML linting results

---

## ✅ Notes
Make sure your HTML files are saved with the .html extension.

You can customize htmlhint rules by creating a .htmlhintrc config file in your project root.

