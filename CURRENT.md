# Current State

_Last updated: 2026-07-13_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL and Docker as the primary development environment.

## Active setup branch

- Working branch: `setup/step-3`
- The branch is the working source of truth for all remaining Step 3 work.
- `main` represents the last merged top-level checkpoint.
- No Step 3 pull request will be created until Step 3.8 cleanup is complete and verified.
- After merge, GitHub automatically deletes the head branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Complete Step 3 by proving that a project stored under `/home/akcoo/projects`:

1. builds and runs through Docker Desktop from Ubuntu;
2. opens correctly through Windows VS Code connected to WSL;
3. works through a Dev Container where appropriate;
4. passes one end-to-end verification cycle without installing project dependencies globally into Ubuntu.

## Current task

**Step 3.8 — end-to-end verification has passed; exact cleanup is authorised next.**

The disposable project passed the direct Docker checkpoint, the Windows VS Code connected-to-WSL checkpoint, and the Dev Container checkpoint. Read-only cleanup inspection identified one active project-specific Dev Container, two project-specific images, one shared `vscode` volume, seven exact project files, and no Step 3.8 launcher log.

The next action is to close the Dev Container window, verify that the exact container stopped, and remove only the identified container, the two identified project-specific images, and the exact disposable project files. Preserve the shared `vscode` volume, base layers, Docker cache, VS Code Server, extensions, and all unrelated resources.

Do not run prune commands, create the Step 3 pull request, merge the branch, or begin Step 4 until cleanup output is reviewed.

## Step 3.8 verified state

### Disposable project

- Path: `/home/akcoo/projects/career-os-step-3-e2e`
- Filesystem: `ext4`
- Owner: `akcoo:akcoo`
- Exact contents:
  - `.devcontainer/devcontainer.json`
  - `.dockerignore`
  - `Dockerfile`
  - `README.md`
  - `app.py`
  - `devcontainer-e2e-check.txt`
  - `vscode-wsl-e2e-check.txt`
- `/home/akcoo/projects` contains exactly this one disposable project.

### Repository-owned runtime

- Base image: `python:3.12.13-slim-bookworm`
- Runtime user: `vscode`
- Direct-image working directory: `/workspace`
- The same repository-owned `Dockerfile` was used for the direct Docker build and the Dev Container build.
- No project dependency was installed into Ubuntu's system Python.

### Direct Docker and VS Code WSL results

- Docker client/server: `29.4.3` / `29.4.3`
- Direct image tag: `career-os-step-3-e2e:local`
- Direct image ID: `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`
- Direct image platform: `linux/amd64`
- Configured user: `vscode`
- Configured working directory: `/workspace`
- Application modes `docker-run` and `vscode-wsl` both passed with Python `3.12.13` at `/usr/local/bin/python`, UID/GID `1000:1000`, and `career_os_step_3_e2e=PASS`.
- Temporary named run containers were removed automatically.
- Visible WSL indicator: `WSL: Ubuntu`.
- The WSL integrated terminal used `/home/akcoo/projects/career-os-step-3-e2e` on `ext4` as user `akcoo`.
- `vscode-wsl-e2e-check.txt` is owned by `akcoo:akcoo`.
- Results:
  - `step_3_8_docker_build=PASS`
  - `step_3_8_docker_run=PASS`
  - `step_3_8_vscode_wsl_verification=PASS`

### Dev Container result

- Visible indicator: `Dev Container: Career OS Step 3 E2E`.
- Explorer showed all five original files and both marker files.
- Container user: `vscode`, UID/GID `1000:1000`, non-root.
- Workspace: `/workspaces/career-os-step-3-e2e`.
- Python: `3.12.13` at `/usr/local/bin/python`.
- `/.dockerenv` was present.
- Workspace mount mapped `/home/akcoo/projects/career-os-step-3-e2e` on `ext4` to `/workspaces/career-os-step-3-e2e`.
- `/workspace/app.py` and `/workspace/README.md` matched the mounted source files.
- `app.py` ran in mode `devcontainer` and returned `career_os_step_3_e2e=PASS`.
- `devcontainer-e2e-check.txt` is owned by `akcoo:akcoo` on Ubuntu and contains `created_from=step-3.8-devcontainer`.
- Results:
  - `step_3_8_devcontainer_identity=PASS`
  - `step_3_8_devcontainer_files=PASS`
  - `step_3_8_devcontainer_application=PASS`
  - `step_3_8_host_ownership=PASS`

## Step 3.8 cleanup inspection

### Active Dev Container

- Exactly one container matched the disposable project bind mount.
- Container ID: `fc44724370b8f956b60b7e341fe04fc7758387f0fd313183d22c08967c5b7ccb`
- Container name: `loving_turing`
- Inspection-time status: `running`
- Inspection-time running flag: `true`
- Image ID: `sha256:05ef729e5d780e71025bf896fa40b53359126b77c679fdc29a91faa58bf1a3e8`
- Image reference: `vsc-career-os-step-3-e2e-946eba5f9159ecc49f572f0fcd987d083b27d846a5b37b76773cf285d5357738`
- Labels identify the exact WSL folder, Dev Container configuration file, and Ubuntu distribution.

### Mounts

The container has:

1. the disposable project bind mount;
2. a transient Docker Desktop Wayland socket bind mount;
3. the named volume `vscode` mounted at `/vscode`.

The `vscode` named volume is shared infrastructure and must be preserved.

### Direct image

- ID: `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`
- Tag: `career-os-step-3-e2e:local`
- Container references: `0`
- Safe to remove after the Dev Container is closed and the exact cleanup preflight passes.

### Generated Dev Container image

- ID: `sha256:05ef729e5d780e71025bf896fa40b53359126b77c679fdc29a91faa58bf1a3e8`
- Tag: `vsc-career-os-step-3-e2e-946eba5f9159ecc49f572f0fcd987d083b27d846a5b37b76773cf285d5357738:latest`
- Container references: `1`, consisting only of the identified Dev Container.
- Safe to remove after that exact container is stopped and removed.

### Preserved infrastructure

- Named volume `vscode` exists and is mounted at `/var/lib/docker/volumes/vscode/_data`.
- Step 3.8 launcher-log count: `0`.
- Do not remove the `vscode` volume.
- Do not run `docker container prune`, `docker image prune`, `docker builder prune`, or `docker system prune`.
- Do not explicitly remove base-image layers or unrelated cache.

## Step 3.7 completion result

- Windows executable interoperability, the VS Code WSL bridge, and required WSL and Dev Containers extensions passed.
- A controlled WSL folder and Dev Container passed identity, runtime, filesystem, mount, UI, and ownership checks.
- Exact Step 3.7 disposable resources were removed while preserving the shared `vscode` volume.
- Result: `step_3_7_cleanup=PASS`.

## Remaining Step 3 sequence

1. Close the Dev Container window and perform guarded exact cleanup of the identified Step 3.8 resources.
2. Verify cleanup and record Step 3 as complete.
3. Create the single Step 3 pull request from `setup/step-3` to `main`.
4. Review and merge the pull request, then verify automatic deletion of `setup/step-3`.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- No Step 3 pull request exists yet.

## Immediate blocker

The Dev Container window is still open and the exact cleanup has not yet been executed.

## Next action

Close the Dev Container VS Code window. From a normal Ubuntu host terminal, run the guarded cleanup preflight. Only if every guard passes, remove the exact stopped container, generated Dev Container image, direct image, and seven project files. Preserve the shared `vscode` volume and all unrelated resources. Return the complete cleanup output.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
