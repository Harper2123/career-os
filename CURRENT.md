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

Create one disposable Python project at `/home/akcoo/projects/career-os-step-3-e2e`. The project will use one repository-owned `Dockerfile` for both a Docker build/run check and the later Dev Container check. It will then be opened through VS Code connected to WSL, reopened in the Dev Container, verified, and removed through exact guarded cleanup.

The first checkpoint is project creation plus Docker build/run from a normal Ubuntu terminal. Do not open VS Code, reopen in a Dev Container, create the Step 3 pull request, or remove the project or image until that checkpoint is reviewed.

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

### Controlled WSL-folder test

- Disposable folder: `/home/akcoo/projects/career-os-vscode-wsl-check`.
- VS Code opened the folder through WSL.
- The Explorer workspace title visibly included a `[WSL: ...]` suffix.
- Explorer showed `README.md` and `vscode-terminal-check.txt`.
- The integrated terminal reported user `akcoo`, home `/home/akcoo`, and the expected Linux workspace path.
- Distribution: Ubuntu.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Architecture: `x86_64`.
- Workspace filesystem: `ext4`.
- `TERM_PROGRAM=vscode`.
- Files created from the WSL-connected terminal were owned by `akcoo:akcoo`.
- Result: `step_3_7_wsl_terminal_verification=PASS`.

### Controlled Dev Container test

- The WSL-hosted folder was reopened using `.devcontainer/devcontainer.json`.
- Visible lower-left indicator: `Dev Container: Career OS Step 3.7 Check`.
- Explorer showed `devcontainer-terminal-check.txt`.
- Container workspace path: `/workspaces/career-os-vscode-wsl-check`.
- Host mount source: `/home/akcoo/projects/career-os-vscode-wsl-check` on `ext4`.
- Container user: `vscode`, UID/GID `1000:1000`.
- The process ran as non-root.
- `/.dockerenv` was present.
- Python version: `3.12.13`.
- Python executable: `/usr/local/bin/python`.
- `TERM_PROGRAM=vscode`.
- `devcontainer-terminal-check.txt` remained owned by `akcoo:akcoo` on Ubuntu.
- Dev Container result: `step_3_7_devcontainer_terminal_verification=PASS`.
- Host ownership result: `step_3_7_host_ownership_verification=PASS`.

### Exact cleanup result

- The stopped disposable container was removed exactly.
- The generated project-specific image was untagged and deleted.
- The shared named volume `vscode` was preserved.
- The launcher log and disposable test folder were removed.
- `/home/akcoo/projects` contains zero entries.
- Docker reports zero remaining containers.
- No prune command was used.
- No base-image layer, cache, shared volume, VS Code Server, extension, or unrelated Docker resource was explicitly removed.
- Result: `step_3_7_cleanup=PASS`.

## Step 3.6 completion result

- Docker Desktop WSL integration is operational.
- Docker client and server both report `29.4.3`; Compose reports `v5.1.3`.
- No competing native Ubuntu Docker Engine packages were found.
- A disposable Python `3.12.13` image built and ran under Docker as a non-root user.
- The Step 3.6 smoke-test container, image, and directory were removed exactly.
- No project dependency was installed globally into Ubuntu.

## Step 3.8 execution sequence

1. Create and inspect the disposable project under `/home/akcoo/projects`.
2. Build and run it through Docker Desktop from Ubuntu using its repository-owned `Dockerfile`.
3. Open the same project through Windows VS Code connected to WSL and verify the Linux terminal and files.
4. Reopen the same project in a Dev Container built from the same `Dockerfile` and verify the runtime, mount, and ownership.
5. Inspect and remove only the exact disposable project, container, generated image, and launcher log while preserving shared infrastructure.
6. Record the completed environment state and prepare the single Step 3 pull request.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.
- No Step 3 pull request exists yet.

## Immediate blocker

The Step 3.8 disposable project has not yet been created or run through Docker.

## Next action

Create the exact disposable project files, validate them, build the tagged image, run the application through Docker Desktop from Ubuntu, and return the complete output. Preserve the project and generated image after the run. Do not open VS Code yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
