# Current State

_Last updated: 2026-07-13_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL and Docker as the primary development environment.

## Active setup branch

- Working branch: `setup/step-3`
- The branch is the working source of truth for all remaining Step 3 substeps.
- `main` represents the last merged top-level checkpoint.
- No Step 3 pull request will be created until Steps 3.6–3.8 satisfy the full Step 3 completion condition.
- After merge, GitHub automatically deletes the head branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Complete Step 3 by proving that a project stored under `/home/akcoo/projects`:

1. builds and runs through Docker Desktop from Ubuntu;
2. opens correctly through Windows VS Code connected to WSL;
3. works through a Dev Container where appropriate;
4. passes one end-to-end verification cycle without installing project dependencies globally into Ubuntu.

## Current task

**Step 3.7 — VS Code connectivity is technically verified; cleanup is pending.**

The WSL-folder and Dev Container checks passed, including terminal, filesystem, Python runtime, workspace mount, ownership, Explorer visibility, and visible remote indicator evidence.

The next action is to close the disposable Dev Container window and inspect the exact associated Docker container, image, mounts, labels, and test-folder contents before removing anything.

Do not begin Step 3.8 or remove unverified Docker resources.

## Step 3.7 verification result

### Windows interoperability and VS Code client

- `/proc/sys/fs/binfmt_misc/WSLInterop` is present.
- `cmd.exe /c ver` exits with status `0`; Windows-process interoperability passes.
- Windows VS Code path: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Windows VS Code version: `1.126.0`, commit `7e7950df89d055b5a378379db9ee14290772148a`, architecture `x64`.
- The Ubuntu `code` command resolves to the Windows VS Code bridge.
- The matching Linux x64 VS Code Server is installed under `~/.vscode-server`.
- Do not delete or reinstall the VS Code Server merely to obtain a cleaner state.

### Required Windows-side extensions

Both required official extensions are present:

- WSL: `ms-vscode-remote.remote-wsl@0.104.3`
- Dev Containers: `ms-vscode-remote.remote-containers@0.459.1`

No extension installation or update is required during Step 3.

### Controlled WSL-folder test

- Test folder: `/home/akcoo/projects/career-os-vscode-wsl-check`.
- VS Code opened the folder through WSL.
- The Explorer workspace title visibly included a `[WSL: ...]` suffix.
- Explorer showed both `README.md` and `vscode-terminal-check.txt`.
- The integrated terminal reported user `akcoo`, home `/home/akcoo`, and the expected Linux workspace path.
- Distribution: Ubuntu.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Architecture: `x86_64`.
- Workspace filesystem: `ext4`.
- `TERM_PROGRAM=vscode`.
- Files created from the WSL-connected terminal are owned by `akcoo:akcoo`.
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
- `README.md`, `vscode-terminal-check.txt`, and `.devcontainer/devcontainer.json` were visible inside the mounted workspace.
- `devcontainer-terminal-check.txt` was created inside the container with numeric ownership `1000:1000`.
- From Ubuntu, the file is owned by `akcoo:akcoo` and contains `created_from=devcontainer-integrated-terminal`.
- Dev Container result: `step_3_7_devcontainer_terminal_verification=PASS`.
- Host ownership result: `step_3_7_host_ownership_verification=PASS`.
- The Dev Container checkpoint is accepted as passed.

## Step 3.6 completion result

- Docker Desktop WSL integration is operational.
- Docker client and server both report `29.4.3`; Compose reports `v5.1.3`.
- No competing native Ubuntu Docker Engine packages were found.
- A full WSL restart restored Windows executable interoperability.
- A disposable Python `3.12.13` image built and ran under Docker as a non-root user.
- The smoke-test container, image, and directory were removed exactly after verification.
- No project dependency was installed globally into Ubuntu.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.

## Remaining Step 3 sequence

1. **Step 3.7:** inspect and remove only the disposable Dev Container test resources, verify cleanup, and close the substep.
2. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
3. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.8 remains unauthorised.

## Immediate blocker

The disposable Dev Container resources and test folder have not yet been inspected for exact cleanup scope.

## Next action

Close the Dev Container VS Code window. From a normal Ubuntu terminal, inspect the exact matching Docker container, image, labels, mounts, and test-folder contents. Do not run Docker prune, remove shared images, or delete the folder until the inspection is reviewed.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
