# Current State

_Last updated: 2026-07-13_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 technical work is complete and awaits the single pull-request checkpoint.

## Active setup branch

- Working branch: `setup/step-3`
- `main` represents the last merged top-level checkpoint.
- Step 3 implementation and verification are complete on the working branch.
- No Step 3 pull request has been created yet.
- After an approved pull request is merged, GitHub is configured to delete the head branch automatically.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Integrate the completed Step 3 work into `main` through one reviewed pull request without beginning Step 4 prematurely.

## Current task

**Step 3 — technical completion verified; pull-request checkpoint pending explicit approval.**

The WSL, Git, Docker Desktop, Windows VS Code connected-to-WSL, Dev Container, Linux-filesystem workspace, non-root Python runtime, ownership, and exact cleanup checks have passed.

The next externally visible action is creation of the single pull request from `setup/step-3` to `main`. Do not create, merge, or close that pull request until Ayush explicitly approves the relevant action.

## Step 3 completion result

### Architecture

- Windows remains the host operating system.
- Ubuntu under WSL 2 is the primary Linux source workspace.
- Active Linux-developed repositories belong under `/home/akcoo/projects`, not `/mnt/c`.
- Docker Desktop with its WSL 2 backend is the default project runtime and dependency-isolation layer.
- Windows VS Code is the editor client, using the WSL and Dev Containers extensions.
- Substantial Python projects use repository-owned container definitions rather than host-global packages, direct project `venv`, Conda, or Miniforge environments.

### WSL and Linux workspace

- Ubuntu 24.04 is available under WSL 2 with systemd.
- Linux user: `akcoo`, UID/GID `1000:1000`, non-root with approved sudo access.
- Project root: `/home/akcoo/projects`.
- Project root filesystem: `ext4`.
- Project root ownership: `akcoo:akcoo`.
- Windows executable interoperability is operational.
- No Linux-developed source project is stored under `/mnt/c`.

### Git and GitHub access

- WSL Git: `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native Ed25519 SSH authentication to GitHub passed.
- Approved Git defaults remain configured.
- SSH-agent persistence was not added; the agent remains session-local.

### Docker Desktop integration

- Docker Desktop WSL integration is operational.
- Docker client/server: `29.4.3` / `29.4.3`.
- Docker Compose: `v5.1.3`.
- No competing native Ubuntu Docker Engine was installed.
- Docker commands from Ubuntu reach Docker Desktop successfully.
- A disposable Python `3.12.13` image built and ran as a non-root user.
- No project dependency was installed into Ubuntu's system Python.

### Windows VS Code and Dev Containers

- Windows VS Code version: `1.126.0`, x64.
- WSL extension: `ms-vscode-remote.remote-wsl@0.104.3`.
- Dev Containers extension: `ms-vscode-remote.remote-containers@0.459.1`.
- The matching Linux VS Code Server is installed under `~/.vscode-server` and must not be removed merely for cleanup.
- A Linux-filesystem folder opened through VS Code with visible indicator `WSL: Ubuntu`.
- The integrated terminal reported the expected Ubuntu user, WSL2 kernel, `ext4` workspace, and `TERM_PROGRAM=vscode`.
- A Dev Container opened with visible indicator `Dev Container: Career OS Step 3 E2E`.
- Container user: `vscode`, UID/GID `1000:1000`, non-root.
- Container Python: `3.12.13` at `/usr/local/bin/python`.
- Files created in the Dev Container remained owned by `akcoo:akcoo` on Ubuntu.

### Step 3.8 end-to-end verification

One disposable project at `/home/akcoo/projects/career-os-step-3-e2e` proved the complete workflow:

1. source stored in the WSL Linux filesystem;
2. image built through Docker Desktop from Ubuntu using a repository-owned `Dockerfile`;
3. application run directly through Docker as UID/GID `1000:1000`;
4. the same project opened through Windows VS Code connected to WSL;
5. the preserved image invoked from the VS Code WSL integrated terminal;
6. the same project reopened in a Dev Container built from the same `Dockerfile`;
7. Python `3.12.13`, non-root execution, workspace mounting, source consistency, and host-side ownership all verified;
8. no host Python project package installed.

Verified results:

- `step_3_8_docker_build=PASS`
- `step_3_8_docker_run=PASS`
- `step_3_8_vscode_wsl_verification=PASS`
- `step_3_8_devcontainer_identity=PASS`
- `step_3_8_devcontainer_files=PASS`
- `step_3_8_devcontainer_application=PASS`
- `step_3_8_host_ownership=PASS`

### Exact cleanup result

Cleanup preflight passed before deletion.

Removed exactly:

- Dev Container `fc44724370b8f956b60b7e341fe04fc7758387f0fd313183d22c08967c5b7ccb`;
- generated Dev Container image `sha256:05ef729e5d780e71025bf896fa40b53359126b77c679fdc29a91faa58bf1a3e8`;
- direct project image `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`;
- the seven disposable project files and their project directory.

Verified afterward:

- the identified container is absent;
- both project-specific images and tags are absent;
- `/home/akcoo/projects` contains zero entries;
- Docker reports zero remaining containers;
- project-named image count is zero;
- shared named volume `vscode` remains present;
- no prune command was used;
- no base-image layer, Docker cache, VS Code Server, extension, or unrelated resource was explicitly removed;
- `step_3_8_cleanup=PASS`.

## Definition of done assessment

The Step 3 completion condition is satisfied:

- WSL 2 is healthy;
- Ubuntu and the non-root Linux identity are configured;
- `~/projects` is the Linux workspace;
- Git identity and GitHub authentication work inside WSL;
- Docker Desktop integration works from Ubuntu;
- a repository-owned Python image builds and runs without host-global project dependencies;
- Windows VS Code opens the Linux project through WSL;
- the same project works through a Dev Container;
- one full end-to-end cycle passed and disposable resources were cleaned exactly.

## Remaining Step 3 repository checkpoint

1. Review the accumulated `setup/step-3` branch changes against `main`.
2. Create the single Step 3 pull request after explicit approval.
3. Review the pull request.
4. Merge only after explicit approval.
5. Verify automatic deletion of `setup/step-3`.
6. Update `CURRENT.md` on `main` before authorising Step 4.

## Immediate blocker

No technical blocker remains. The only blocker is the required explicit approval for the externally visible pull-request action.

## Next action

Wait for the exact instruction to proceed with the Step 3 pull request. Do not begin Step 4, create or merge a pull request, or delete the branch before that approval.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
