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

**Step 3.7 — VS Code connectivity is complete.**

Windows VS Code, WSL connectivity, Linux workspace paths, the integrated terminal, Dev Containers, container-side Python execution, host-side ownership preservation, and exact cleanup all passed.

Step 3.8 remains gated and has not begun.

## Step 3.7 verification result

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

Cleanup preflight passed for the exact disposable resources:

- container ID `4e1ca1a45fa59baf2a1d5f468760001e80864df3059e3f1930b9ac807f5f1aa1`;
- project-specific generated image ID `sha256:5059f6d7370947f51aeb2d1aabf17b703636839bd192dddc4085adf9c6775b41`;
- folder `/home/akcoo/projects/career-os-vscode-wsl-check`;
- launcher log `~/.step-3-7-code-open.log`.

Verified cleanup results:

- the stopped disposable container was removed exactly;
- the generated project-specific image was untagged and deleted;
- the shared named volume `vscode` was preserved;
- the launcher log was removed;
- the disposable test folder was removed;
- `/home/akcoo/projects` contains zero entries;
- Docker reports zero remaining containers;
- no prune command was used;
- no base-image layer, cache, shared volume, VS Code Server, extension, or unrelated Docker resource was explicitly removed;
- result: `step_3_7_cleanup=PASS`.

## Step 3.6 completion result

- Docker Desktop WSL integration is operational.
- Docker client and server both report `29.4.3`; Compose reports `v5.1.3`.
- No competing native Ubuntu Docker Engine packages were found.
- A disposable Python `3.12.13` image built and ran under Docker as a non-root user.
- The Step 3.6 smoke-test container, image, and directory were removed exactly.
- No project dependency was installed globally into Ubuntu.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- Approved Git defaults remain configured.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.
- No Step 3 pull request exists yet.

## Remaining Step 3 sequence

1. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
2. Create one pull request from `setup/step-3` to `main`.
3. Review and merge the pull request.
4. Verify automatic deletion of `setup/step-3`.

Step 3.8 remains unauthorised until Ayush explicitly says `Proceed to Step 3.8`.

## Immediate blocker

- No technical blocker remains from Step 3.7.
- Step 3.8 is waiting for explicit approval.

## Next action

Wait for the exact command `Proceed to Step 3.8`.

Do not create another test project, create the Step 3 pull request, merge the branch, or begin later setup steps before that approval.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
