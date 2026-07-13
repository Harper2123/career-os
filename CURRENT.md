# Current State

_Last updated: 2026-07-13_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL and Docker as the primary development environment.

## Active setup branch

- Working branch: `setup/step-3`
- The branch is the working source of truth for all remaining Step 3 work.
- `main` represents the last merged top-level checkpoint.
- No Step 3 pull request will be created until Step 3.8 satisfies the full Step 3 completion condition.
- After merge, GitHub automatically deletes the head branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Complete Step 3 by proving that a project stored under `/home/akcoo/projects`:

1. builds and runs through Docker Desktop from Ubuntu;
2. opens correctly through Windows VS Code connected to WSL;
3. works through a Dev Container where appropriate;
4. passes one end-to-end verification cycle without installing project dependencies globally into Ubuntu.

## Current task

**Step 3.8 — end-to-end environment verification is active.**

The disposable project passed both the direct Docker checkpoint and the Windows VS Code connected-to-WSL checkpoint. The next action is to reopen the same project in a Dev Container built from the same repository-owned `Dockerfile`, verify the runtime, workspace mount, files, application execution, and host-side ownership, then preserve all resources until exact cleanup scope is inspected.

Do not remove the project or images, create the Step 3 pull request, merge the branch, or begin Step 4 until the Dev Container checkpoint and exact cleanup are reviewed.

## Step 3.8 verified state

### Disposable project

- Path: `/home/akcoo/projects/career-os-step-3-e2e`
- Project filesystem: `ext4`
- Project owner: `akcoo:akcoo`
- Original files:
  - `.devcontainer/devcontainer.json`
  - `.dockerignore`
  - `Dockerfile`
  - `README.md`
  - `app.py`
- WSL marker file: `vscode-wsl-e2e-check.txt`
- `/home/akcoo/projects` contains exactly this one disposable project.

### Repository-owned runtime definition

- Base image: `python:3.12.13-slim-bookworm`
- Runtime user: `vscode`
- Working directory in the direct Docker image: `/workspace`
- The same `Dockerfile` is used by the direct Docker build and the Dev Container definition.
- No project dependency was installed into Ubuntu's system Python.

### Docker build and direct run

- Docker client/server: `29.4.3` / `29.4.3`
- Tagged image: `career-os-step-3-e2e:local`
- Image ID: `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`
- Platform: `linux/amd64`
- Configured image user: `vscode`
- Configured working directory: `/workspace`
- Application mode: `docker-run`
- Python: `3.12.13` at `/usr/local/bin/python`
- UID/GID: `1000:1000`
- Non-root, Python-version, and test-mode checks passed.
- The named run container was removed automatically.
- The project directory and tagged image remain available.
- Docker reported zero remaining containers after the run.
- Results:
  - `step_3_8_docker_build=PASS`
  - `step_3_8_docker_run=PASS`

### Windows VS Code connected to WSL

- Visible lower-left indicator: `WSL: Ubuntu`.
- Explorer showed all five original project files and `vscode-wsl-e2e-check.txt`.
- Integrated-terminal user: `akcoo`.
- Home: `/home/akcoo`.
- Workspace: `/home/akcoo/projects/career-os-step-3-e2e`.
- Distribution: Ubuntu.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Workspace filesystem: `ext4`.
- Workspace owner: `akcoo:akcoo`.
- `TERM_PROGRAM=vscode`.
- The preserved image was invoked from the VS Code WSL integrated terminal with mode `vscode-wsl`.
- The application again ran with Python `3.12.13` at `/usr/local/bin/python` as UID/GID `1000:1000` and returned `career_os_step_3_e2e=PASS`.
- The temporary named container was removed automatically.
- `vscode-wsl-e2e-check.txt` contains `created_from=vscode-wsl-integrated-terminal` and is owned by `akcoo:akcoo`.
- Result: `step_3_8_vscode_wsl_verification=PASS`.

## Step 3.7 completion result

- Windows executable interoperability, the VS Code WSL bridge, and the matching VS Code Server passed.
- Required Windows-side WSL and Dev Containers extensions are present.
- A controlled Linux folder opened through WSL with the expected Ubuntu identity, WSL2 kernel, `ext4` filesystem, and ownership.
- The folder reopened successfully in a Dev Container as non-root user `vscode`, Python `3.12.13`, UID/GID `1000:1000`.
- Files created in the container remained owned by `akcoo:akcoo` on Ubuntu.
- The exact disposable Step 3.7 container, generated image, launcher log, and folder were removed.
- The shared `vscode` named volume was preserved.
- No prune command or unrelated cleanup was performed.
- Result: `step_3_7_cleanup=PASS`.

## Step 3.8 remaining sequence

1. Reopen `/home/akcoo/projects/career-os-step-3-e2e` in a Dev Container built from the same `Dockerfile` and verify the container identity, Python runtime, mounted files, application execution, and host ownership.
2. Inspect the exact Dev Container, all generated project-specific images, mounts, labels, shared volumes, launcher log, and project contents.
3. Remove only the exact disposable project, containers, project-specific images, and launcher log while preserving shared infrastructure, base layers, and unrelated cache.
4. Record Step 3 as complete.
5. Create the single Step 3 pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.
- No Step 3 pull request exists yet.

## Immediate blocker

The Step 3.8 Dev Container checkpoint has not yet been completed.

## Next action

From the existing WSL-connected VS Code window, run **Dev Containers: Reopen in Container**. In the resulting container terminal, verify the non-root `vscode` user, Python `3.12.13`, mounted project files, the `/.dockerenv` marker, execution of `app.py` with test mode `devcontainer`, and creation of one marker file that remains owned by `akcoo:akcoo` from the Ubuntu host. Preserve the project, container, images, and marker files afterward for exact cleanup inspection.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
