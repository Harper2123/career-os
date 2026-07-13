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

The disposable project has been created and its Docker build/run checkpoint passed. The next action is to open the same project through Windows VS Code connected to WSL, verify Linux-side terminal identity and files, run the already-built image from that integrated terminal, and create one ownership marker file.

Do not reopen in a Dev Container, remove the project or image, create the Step 3 pull request, or begin Step 4 until the WSL-connected VS Code checkpoint is reviewed.

## Step 3.8 Docker checkpoint

### Disposable project

- Path: `/home/akcoo/projects/career-os-step-3-e2e`
- Files:
  - `.devcontainer/devcontainer.json`
  - `.dockerignore`
  - `Dockerfile`
  - `README.md`
  - `app.py`
- Project owner: `akcoo:akcoo`
- Project filesystem: `ext4`
- Project-root entry count after creation: `1`
- Python syntax, Dev Container JSON, pinned base image, non-root Docker user definition, and exact file count all passed.

### Repository-owned runtime definition

- Base image: `python:3.12.13-slim-bookworm`
- Runtime user: `vscode`
- Working directory: `/workspace`
- The same `Dockerfile` is reserved for both the Docker test and later Dev Container test.
- `.dockerignore` excludes Git metadata, Dev Container configuration, caches, environment files, virtual environments, and logs from the image build context.

### Docker build

- Docker client/server: `29.4.3` / `29.4.3`
- Tagged image: `career-os-step-3-e2e:local`
- Image ID: `sha256:6fd187b54da3d191b90dcd975cab995743c601ed2a39a4966f825dcde5c86a06`
- Platform: `linux/amd64`
- Configured image user: `vscode`
- Configured working directory: `/workspace`
- Result: `step_3_8_docker_build=PASS`

### Docker application run

The application ran with:

- mode: `docker-run`
- Python version: `3.12.13`
- Python executable: `/usr/local/bin/python`
- working directory: `/workspace`
- UID/GID: `1000:1000`
- non-root execution: passed
- Python 3.12 check: passed
- test-mode check: passed
- application result: `career_os_step_3_e2e=PASS`

Post-run verification:

- the named run container was removed automatically;
- the generated image remains available;
- the project directory remains available;
- `/home/akcoo/projects` contains exactly the one disposable project;
- Docker reports zero remaining containers;
- no host Python project package was installed;
- result: `step_3_8_docker_run=PASS`.

## Step 3.7 completion result

### Windows interoperability and VS Code client

- `/proc/sys/fs/binfmt_misc/WSLInterop` is present.
- `cmd.exe /c ver` exits with status `0`; Windows-process interoperability passes.
- Windows VS Code path: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Windows VS Code version: `1.126.0`, commit `7e7950df89d055b5a378379db9ee14290772148a`, architecture `x64`.
- The Ubuntu `code` command resolves to the Windows VS Code bridge.
- The matching Linux x64 VS Code Server is installed under `~/.vscode-server`.
- Running `code --version` installed or updated the matching VS Code Server; it was therefore not a read-only action.
- Do not delete or reinstall the VS Code Server merely to obtain a cleaner state.

### Required Windows-side extensions

Both required official extensions are present:

- WSL: `ms-vscode-remote.remote-wsl@0.104.3`
- Dev Containers: `ms-vscode-remote.remote-containers@0.459.1`

No extension installation or update was required.

### Controlled WSL-folder and Dev Container checks

- Windows VS Code opened a Linux-filesystem folder through WSL.
- The integrated terminal reported the expected Ubuntu identity, WSL2 kernel, `ext4` workspace, and `TERM_PROGRAM=vscode`.
- Files created through the WSL terminal were owned by `akcoo:akcoo`.
- The folder reopened successfully in a Dev Container.
- Visible Dev Container indicator: `Dev Container: Career OS Step 3.7 Check`.
- Container user: `vscode`, UID/GID `1000:1000`, running non-root.
- Python: `3.12.13` at `/usr/local/bin/python`.
- Files created inside the container remained owned by `akcoo:akcoo` on Ubuntu.
- WSL terminal, Dev Container terminal, and host ownership checks all passed.

### Exact cleanup

- The stopped disposable Step 3.7 container and project-specific image were removed exactly.
- The shared named volume `vscode` was preserved.
- The launcher log and disposable folder were removed.
- No prune command, unrelated cleanup, VS Code Server deletion, or extension removal was performed.
- Result: `step_3_7_cleanup=PASS`.

## Step 3.8 remaining sequence

1. Open `/home/akcoo/projects/career-os-step-3-e2e` through Windows VS Code connected to WSL and verify the terminal, project files, Docker invocation, and host ownership.
2. Reopen the same project in a Dev Container built from the same repository-owned `Dockerfile` and verify the runtime, mount, files, and ownership.
3. Inspect and remove only the exact disposable project, generated containers/images, and launcher log while preserving shared infrastructure and unrelated cache/layers.
4. Record the completed environment state.
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

The Step 3.8 WSL-connected VS Code checkpoint has not yet been completed.

## Next action

Open the existing project through VS Code connected to WSL. From the integrated terminal, verify the Linux workspace, confirm all five project files, run the preserved `career-os-step-3-e2e:local` image with test mode `vscode-wsl`, and create one marker file whose Ubuntu ownership is `akcoo:akcoo`. Preserve the project and image afterward. Do not reopen in a Dev Container yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
