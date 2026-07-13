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

The disposable project passed the direct Docker checkpoint, the Windows VS Code connected-to-WSL checkpoint, and the Dev Container identity, file, and application checks. The remaining evidence for the Dev Container checkpoint is host-side ownership verification from a separate normal Ubuntu terminal plus the visible Dev Container indicator and Explorer confirmation.

The attempted host ownership command was run inside the Dev Container, where `$HOME` is `/home/vscode`; it therefore checked `/home/vscode/projects/...` and correctly reported `host_marker_presence_check=FAIL`. This does not indicate a file or ownership failure. Run the ownership check from a normal Ubuntu host terminal while keeping the Dev Container open.

Do not remove the project or images, close the Dev Container, create the Step 3 pull request, merge the branch, or begin Step 4 until host ownership and UI evidence are reviewed.

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
- Dev Container marker file: `devcontainer-e2e-check.txt`
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

### Dev Container

Verified inside the Dev Container:

- Container terminal user: `vscode`.
- UID/GID: `1000:1000`.
- Home: `/home/vscode`.
- Workspace: `/workspaces/career-os-step-3-e2e`.
- Workspace basename: `career-os-step-3-e2e`.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Architecture: `x86_64`.
- `TERM_PROGRAM=vscode`.
- Python: `3.12.13` at `/usr/local/bin/python`.
- `/.dockerenv` is present.
- Non-root user, workspace path, and Python checks passed.
- All original project files plus `vscode-wsl-e2e-check.txt` are visible in the mounted workspace.
- `/workspace/app.py` and `/workspace/README.md` match the mounted source files.
- Workspace mount maps `/home/akcoo/projects/career-os-step-3-e2e` on `ext4` to `/workspaces/career-os-step-3-e2e`.
- `app.py` ran with mode `devcontainer`, Python `3.12.13`, UID/GID `1000:1000`, and returned `career_os_step_3_e2e=PASS`.
- `devcontainer-e2e-check.txt` was created with numeric ownership `1000:1000` and contains `created_from=step-3.8-devcontainer`.
- Results:
  - `step_3_8_devcontainer_identity=PASS`
  - `step_3_8_devcontainer_files=PASS`
  - `step_3_8_devcontainer_application=PASS`

Pending Dev Container evidence:

- run the host ownership check from a separate normal Ubuntu terminal;
- report the exact visible lower-left Dev Container indicator;
- confirm Explorer shows all five original files, `vscode-wsl-e2e-check.txt`, and `devcontainer-e2e-check.txt`.

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

1. Complete host-side ownership and UI verification for the active Dev Container.
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

The Dev Container host-side ownership check was executed from the wrong terminal context. It must be run from a separate normal Ubuntu host terminal while the Dev Container remains open.

## Next action

From a normal Ubuntu terminal whose prompt starts with `akcoo@MSI`, verify that `/home/akcoo/projects/career-os-step-3-e2e/devcontainer-e2e-check.txt` exists, is owned by `akcoo:akcoo`, and contains `created_from=step-3.8-devcontainer`. Also return the exact visible Dev Container indicator and Explorer file confirmation. Preserve all resources afterward for cleanup inspection.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
