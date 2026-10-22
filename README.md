# Gitflow Simulation & Industrial Version Control Pipeline

## Executive Summary
This repository contains a full-scale simulation of the **Gitflow Branching Strategy** and continuous delivery automation built for the **DataGrokr Pre-Learning Program (PLP) Week 7-8 Capstone Project**[cite: 3, 16, 17]. The workflow establishes clean branch separation, strict pull request enforcement, hotfix isolation, pre-commit hook validation, and automated continuous integration using GitHub Actions.

---

## Technical Architecture & Branch Strategy

### 1. Main Branch (`main`)
* Serves as the primary production-ready line.
* Accepts commits solely via explicit non-fast-forward (`--no-ff`) merges from release and hotfix branches[cite: 16, 17].

### 2. Feature Isolation (`feature/login`)
* Created off the target baseline to develop independent software modules (`login` authentication function)[cite: 16, 17].
* Integrated back using explicit commit tracking (`git merge feature/login --no-ff`)[cite: 16, 17].

### 3. Release Lifecycle (`release/v1.0.0`)
* Handles version tagging (`v1.0.0`), documentation updates, and deployment preparation without blocking ongoing development[cite: 16, 17].

### 4. Production Patching (`hotfix/critical-bug`)
* Emergency branch created directly from production state to patch critical security issues (`app.py` patch) before immediate re-integration[cite: 16, 17].

---

## Automation & Quality Controls

### Pre-Commit Validation Hook
* Custom shell script located under `.git/hooks/pre-commit`[cite: 16, 17].
* Intercepts every local commit execution, ensuring code style and integrity rules pass before registering history[cite: 16, 17].

### GitHub Actions CI Workflow
* Automated pipeline defined in `.github/workflows/ci.yml`[cite: 16, 17].
* Triggers on every `push` event to execute build verification inside an isolated `ubuntu-latest` runner environment[cite: 16, 17].

---

## Local Execution Logs

To verify the non-linear execution graph and branch history locally, run:
```bash
git log --oneline --graph --all
```
