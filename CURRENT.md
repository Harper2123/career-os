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

**Step 3.8 — end-to-end verification has passed; cleanup inspection is active.**

The disposable project passed the direct Docker checkpoint, the Windows VS Code connected-to-WSL checkpoint, and the Dev Container checkpoint, including host-side ownership and UI evidence.

The next action is read-only inspection of the exact active Dev Container, direct Docker image, generated Dev Container image, mounts, labels, shared volumes, project contents, and any launcher log. Preserve all resources until the inspection is reviewed.

Do not remove anything, run prune commands, create the Step 3 pull request, merge the branch, or begin Step 4 yet.

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
- WSL marker: `vscode-wsl-e2e-check.txt`
- Dev Container marker: `devcontainer-e2e-check.txt`
- `/home/akcoo/projects` contains exactly this one disposable project.

### Repository-owned runtime

- Base image: `python:3.12.13-slim-bookworm`
- Runtime user: `vscode`
- Direct-image working directory: `/workspace`
- The same repository-owned `Dockerfile` is used for the direct Docker build and Dev Container build.
- No project dependency was installed into Ubuntu's system Python.

### Direct Docker build and run

- Docker client/server: `29.4.3` / `29.4.3`
- Tagged image: `career-os-step-3-e2e:local`
- Image ID: `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`
- Platform: `linux/amd64`
- Configured image user: `vscode`
- Configured working directory: `/workspace`
- Application modes `docker-run` and `vscode-wsl` both passed with Python `3.12.13` at `/usr/local/bin/python`, UID/GID `1000:1000`, and `career_os_step_3_e2e=PASS`.
- Temporary named run containers were removed automatically.
- The project directory and direct image remain available.
- Results:
  - `step_3_8_docker_build=PASS`
  - `step_3_8_docker_run=PASS`
  - `step_3_8_vscode_wsl_verification=PASS`

### Windows VS Code connected to WSL

- Visible indicator: `WSL: Ubuntu`.
- Explorer showed all five original files and `vscode-wsl-e2e-check.txt`.
- Integrated-terminal user: `akcoo`.
- Workspace: `/home/akcoo/projects/career-os-step-3-e2e`.
- Distribution: Ubuntu.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Workspace filesystem: `ext4`.
- Workspace owner: `akcoo:akcoo`.
- `TERM_PROGRAM=vscode`.
- `vscode-wsl-e2e-check.txt` contains `created_from=vscode-wsl-integrated-terminal` and is owned by `akcoo:akcoo`.

### Dev Container

Verified inside the Dev Container:

- Visible indicator: `Dev Container: Career OS Step 3 E2E`.
- Explorer showed all five original files, `vscode-wsl-e2e-check.txt`, and `devcontainer-e2e-check.txt`.
- Container terminal user: `vscode`.
- UID/GID: `1000:1000`.
- Home: `/home/vscode`.
- Workspace: `/workspaces/career-os-step-3-e2e`.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Architecture: `x86_64`.
- `TERM_PROGRAM=vscode`.
- Python: `3.12.13` at `/usr/local/bin/python`.
- `/.dockerenv` is present.
- All original project files plus the WSL marker are visible in the mounted workspace.
- `/workspace/app.py` and `/workspace/README.md` match the mounted source files.
- The workspace mount maps `/home/akcoo/projects/career-os-step-3-e2e` on `ext4` to `/workspaces/career-os-step-3-e2e`.
- `app.py` ran in mode `devcontainer` and returned `career_os_step_3_e2e=PASS`.
- `devcontainer-e2e-check.txt` contains `created_from=step-3.8-devcontainer`.
- Inside the container its numeric ownership is `1000:1000`.
- From a separate normal Ubuntu terminal it resolves to `/home/akcoo/projects/career-os-step-3-e2e/devcontainer-e2e-check.txt` and is owned by `akcoo:akcoo` (`1000:1000`).
- Results:
  - `step_3_8_devcontainer_identity=PASS`
  - `step_3_8_devcontainer_files=PASS`
  - `step_3_8_devcontainer_application=PASS`
  - `step_3_8_host_ownership=PASS`

## Step 3.7 completion result

- Windows executable interoperability, the VS Code WSL bridge, and the matching VS Code Server passed.
- Required Windows-side WSL and Dev Containers extensions are present.
- A controlled Linux folder opened through WSL and then in a Dev Container with the expected identity, runtime, filesystem, and ownership.
- The exact Step 3.7 disposable resources were removed while preserving the shared `vscode` volume.
- No prune command or unrelated cleanup was performed.
- Result: `step_3_7_cleanup=PASS`.

## Step 3.8 remaining sequence

1. Inspect the exact active Dev Container, direct image, generated Dev Container image, mounts, labels, shared volumes, launcher log, and project contents.
2. Close the Dev Container and remove only the exact disposable project, containers, project-specific images, and launcher log while preserving shared infrastructure, base layers, and unrelated cache.
3. Verify cleanup and record Step 3 as complete.
4. Create the single Step 3 pull request from `setup/step-3` to `main`.
5. Review and merge the pull request, then verify automatic deletion of `setup/step-3`.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.
- No Step 3 pull request exists yet.

## Immediate blocker

The exact disposable cleanup scope has not yet been inspected.

## Next action

From a separate normal Ubuntu host terminal, inspect the active Dev Container and all project-specific Docker resources without removing anything. Preserve the Dev Container window, project files, direct image, generated image, and shared `vscode` volume until review.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
