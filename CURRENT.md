# Current State

_Last updated: 2026-07-13_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` represents the last merged top-level checkpoint.
- All Step 4 substeps will be completed on this branch.
- One pull request will be created only after the full Step 4 completion condition is verified.
- Unrelated work must not be added to this branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The setup must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.1: read-only VS Code inventory.**

Collect the current Windows VS Code CLI capabilities, installed profiles, installed extensions, selected safe settings, WSL-side VS Code Server state, and relevant extension state before installing, removing, enabling, disabling, or changing anything.

Do not alter profiles, extensions, settings, keybindings, snippets, workspace files, WSL configuration, Docker configuration, or shell configuration during Step 4.1.

## Step 4 completion condition

Step 4 is complete only when all of the following work consistently from Windows VS Code using WSL:

- Python editing and execution through the approved container workflow;
- Jupyter notebooks where justified;
- Markdown editing and preview;
- test discovery and execution;
- Git inspection and operations;
- integrated Linux terminal commands;
- Docker and Dev Container workflows;
- the minimum approved extension and profile set;
- automatic AI completion disabled by default.

This completion condition comes from `plans/setup-roadmap.md`.

## Step 4 staged sequence

1. **Step 4.1, inventory:** collect the current state without changing it.
2. **Step 4.2, design:** define the minimum profile, extension, and settings architecture from evidence.
3. **Step 4.3, Windows profile:** create or configure only the approved Windows-side profile and local extensions.
4. **Step 4.4, WSL profile:** configure only the approved WSL-side tools and remote extensions.
5. **Step 4.5, editor workflows:** validate Python, notebooks, Markdown, tests, Git, and terminal work.
6. **Step 4.6, container workflows:** validate Docker and Dev Containers through the configured editor.
7. **Step 4.7, AI completion boundary:** verify automatic AI completion remains disabled by default.
8. **Step 4.8, end-to-end test and cleanup:** run one harmless complete workflow, record evidence, and remove only disposable artifacts.
9. Review and create one Step 4 pull request only after all checks pass.

Substep details may be refined after the read-only inventory. Later substeps are not authorised merely by being listed here.

## Governing constraints

- Prefer the minimum useful configuration.
- Do not add extensions merely because they are popular.
- Do not duplicate capabilities already supplied by VS Code, WSL, Docker Desktop, or a repository-owned container.
- Keep automatic AI completion disabled by default.
- GitHub Copilot must not provide automatic code completions unless a future explicit decision changes that boundary.
- Preserve the Step 3 architecture: Windows as host, Ubuntu WSL as the primary Linux workspace, and Docker Desktop as the project runtime.
- Do not install project dependencies into Ubuntu's system Python.
- Do not begin Step 5 Git and GitHub workflow practice during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.
- Excessive VS Code customisation remains excluded from Career OS v1.

## Verified Step 3 baseline

- Ubuntu 24.04 under WSL 2 is healthy with systemd.
- Linux user `akcoo` is non-root with UID/GID `1000:1000`.
- Linux project root is `/home/akcoo/projects` on `ext4`.
- WSL Git and GitHub SSH authentication pass.
- Docker Desktop WSL integration works from Ubuntu.
- Windows VS Code version `1.126.0` previously opened a Linux project through WSL.
- WSL extension `ms-vscode-remote.remote-wsl@0.104.3` was present during Step 3.
- Dev Containers extension `ms-vscode-remote.remote-containers@0.459.1` was present during Step 3.
- A repository-owned Python `3.12.13` image ran directly and through a Dev Container as a non-root user.
- Host-side ownership remained correct.
- Disposable Step 3 artifacts were removed exactly.

## Immediate blocker

No technical blocker is known. The current configuration has not yet been inventoried under Step 4.

## Next action

Run the approved read-only Windows and WSL VS Code inventory commands. Return the complete outputs for review. Do not make any VS Code change yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
