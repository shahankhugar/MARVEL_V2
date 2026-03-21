# Task 03 — Working with GitHub

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is GitHub?

GitHub is a platform for hosting and collaborating on code using Git. Git is a version control system — it tracks every change made to a codebase, lets multiple people work on the same project without overwriting each other's work, and allows you to go back to any previous version of the code at any time.

GitHub adds a web interface and collaboration tools on top of Git. The three most important features covered in this task are Issues, Pull Requests, and GitHub Actions.

---

## Key Concepts

**Repository** — a folder for your project that Git tracks. Every change you make is saved as a commit with a message describing what you did.

**Fork** — your own personal copy of someone else's repository. You fork a repo when you want to make changes to it without affecting the original. The changes live in your fork until you propose to merge them back.

**Branch** — a separate line of development inside a repo. You make changes on a branch so the main codebase stays untouched until your work is reviewed and approved.

**Commit** — a saved snapshot of your changes with a message. Every commit has a unique ID so you can track exactly what changed and when.

**Pull Request (PR)** — a formal proposal to merge your changes from your fork (or branch) into the original repository. Other contributors can review the code, leave comments, and either approve or request changes before it gets merged.

**Issue** — a way to report a bug, request a feature, or discuss something about the project. Issues are tracked separately from code but can be linked to pull requests.

**GitHub Actions** — an automation system built into GitHub. You write a workflow file (YAML) that runs automatically when something happens — like when a PR is opened. In this task, the repo had a workflow that ran tests automatically on every pull request to check whether the code was correct.

---

## What the Task Required

The UVCE-Marvel/git-task repository had a bug in `main.py`. The `add` function was incorrectly returning `a + b + 1` instead of `a + b`, causing the automated tests in `testing.py` to fail. GitHub Actions was set up to run these tests on every pull request, so the failing tests were visible directly in the PR checks.

The task was to find the bug, fix it, and submit a pull request proposing the fix to the original repository.

---

## What I Did

**Step 1 — Forked the repository**
I forked `UVCE-Marvel/git-task` to my own GitHub account, creating a copy at `shahankhugar/git-task` that I could freely edit.

**Step 2 — Identified the bug**
In `main.py`, the `add` function had an off-by-one error — it was returning `a + b + 1` instead of the correct `a + b`. This caused the test in `testing.py` to fail because the expected output didn't match the actual output.

**Step 3 — Fixed the code**
I edited `main.py` directly on GitHub, removed the erroneous `+ 1`, and committed the change with the message: `Fix add function to return correct sum`.

**Step 4 — Opened a Pull Request**
I opened PR #275 from `shahankhugar:main` to `UVCE-Marvel:main`, describing the fix. The PR triggers the GitHub Actions workflow, which runs the tests automatically to verify the fix is correct.

---

## How GitHub Actions fits in

The repo has a workflow file inside `.github/workflows/` that runs `testing.py` automatically every time a pull request is opened or updated. This is CI — Continuous Integration. Instead of someone manually checking whether your code works, the tests run automatically and the result is shown directly on the PR page as a pass or fail. This is standard practice in real-world software development.

---

## Pull Request

https://github.com/UVCE-Marvel/git-task/pull/275
