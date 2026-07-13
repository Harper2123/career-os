# Current State

_Last updated: 2026-07-12_

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

**Step 3.7 — VS Code connectivity is active and technically verified.**

The WSL-folder and Dev Container terminal checks passed. The remaining evidence is the exact visible Dev Container indicator text and confirmation that `devcontainer-terminal-check.txt` appears in Explorer. Preserve the existing test folder and container until that UI evidence is reviewed.

Do not install or update extensions, begin Step 3.8, or remove the test folder or Dev Container resources yet.

## Step 3.7 inspection result

### Windows interoperability and VS Code client

- `/proc/sys/fs/binfmt_misc/WSLInterop` is present.
- `cmd.exe /c ver` exits with status `0`; Windows-process interoperability passes.
- Windows VS Code was found at `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Windows VS Code version is `1.126.0`, commit `7e7950df89d055b5a378379db9ee14290772148a`, architecture `x64`.

### WSL code bridge and VS Code Server

- The Ubuntu `code` command resolves to the Windows VS Code shell bridge under `/mnt/c/Users/akcoo/AppData/Local/Programs/Microsoft VS Code/bin/code`.
- Running `code --version` succeeded but also installed or updated the matching Linux x64 VS Code Server. The earlier description of this command as read-only was incorrect.
- The active VS Code Server commit directory is `7e7950df89d055b5a378379db9ee14290772148a`.
- `~/.vscode-server` is present, contains one server commit directory and 38 extension directories, and reported approximately `1.9G` disk usage.
- `~/.vscode-server-insiders` is absent.
- Do not delete or reinstall the server merely to obtain a cleaner state.

### Required Windows-side extensions

The Windows client extension inventory contains 36 extensions. Both required official extensions are present:

- WSL: `ms-vscode-remote.remote-wsl@0.104.3`
- Dev Containers: `ms-vscode-remote.remote-containers@0.459.1`

The earlier WSL-side `code --list-extensions` output did not show these local Windows extensions and is not evidence that they are absent. No extension installation is required.

The interactive PowerShell `else` errors occurred because `else` was entered as a separate statement after the completed `if` block. Both positive branches had already executed and printed the required extension evidence.

### Docker and project root

- Docker client/server connectivity passes with version `29.4.3` on both sides.
- `/home/akcoo/projects` resolves correctly, resides on `ext4`, is owned by `akcoo:akcoo`, and has mode `755`.

### Controlled WSL-folder test

- Test folder: `/home/akcoo/projects/career-os-vscode-wsl-check`.
- The VS Code integrated terminal reported user `akcoo`, home `/home/akcoo`, and working directory `/home/akcoo/projects/career-os-vscode-wsl-check`.
- Distribution is Ubuntu, kernel is `6.6.114.1-microsoft-standard-WSL2`, architecture is `x86_64`, and the workspace filesystem is `ext4`.
- The directory is owned by `akcoo:akcoo`.
- `TERM_PROGRAM=vscode`, confirming the shell ran inside the VS Code integrated terminal.
- `VSCODE_REMOTE_NAME` was unset; this does not invalidate the stronger Linux path, WSL kernel, filesystem, and terminal evidence.
- User, path, filesystem, and kernel checks all passed.
- `vscode-terminal-check.txt` was created from the integrated terminal, is owned by `akcoo:akcoo`, and contains `created_from=vscode-integrated-terminal`.
- Terminal result: `step_3_7_wsl_terminal_verification=PASS`.
- The supplied VS Code screenshot shows both `README.md` and `vscode-terminal-check.txt` in Explorer.
- The Explorer workspace title visibly includes a truncated `[WSL: ...]` suffix, confirming the window is attached through WSL. The lower-left status-bar text itself was outside the screenshot crop, so no exact status-bar wording is claimed.
- The WSL-folder checkpoint is accepted as passed based on the combined UI and terminal evidence.

### Controlled Dev Container test

- The existing WSL-hosted test folder was reopened in a Dev Container using `.devcontainer/devcontainer.json`.
- The Dev Container workspace path is `/workspaces/career-os-vscode-wsl-check`.
- The workspace mount maps from `/home/akcoo/projects/career-os-vscode-wsl-check` on `ext4`.
- The integrated terminal user is `vscode`, UID/GID `1000:1000`, with home `/home/vscode`.
- The process runs as a non-root user.
- `TERM_PROGRAM=vscode` confirms the shell runs inside the VS Code integrated terminal.
- `/.dockerenv` is present, confirming container execution.
- Python reports version `3.12.13` at `/usr/local/bin/python`.
- `README.md`, `vscode-terminal-check.txt`, and `.devcontainer/devcontainer.json` were all visible from inside the mounted workspace.
- `devcontainer-terminal-check.txt` was created inside the Dev Container with numeric ownership `1000:1000`.
- From the normal Ubuntu host, that file resolves to `/home/akcoo/projects/career-os-vscode-wsl-check/devcontainer-terminal-check.txt`, is owned by `akcoo:akcoo`, and contains `created_from=devcontainer-integrated-terminal`.
- Dev Container terminal result: `step_3_7_devcontainer_terminal_verification=PASS`.
- Host ownership result: `step_3_7_host_ownership_verification=PASS`.
- `VSCODE_REMOTE_NAME` was unset; this does not invalidate the container, mount, user, Python, and ownership evidence.
- Exact visible Dev Container indicator text and Explorer visibility of `devcontainer-terminal-check.txt` are still awaiting user report.

## Step 3.6 completion result

### Docker Desktop integration

- Docker CLI is available through Docker Desktop's WSL integration.
- Docker client and server report version `29.4.3`.
- Docker Compose reports `v5.1.3`.
- The server identifies as Docker Desktop on `docker-desktop`.
- No competing native Ubuntu Docker Engine packages were found.

### Home-directory cleanup

- `/home/akcoo/datacamp` is absent.
- `/home/akcoo/quant-data-journey` is absent.
- `/home/akcoo/voice-customer-support-ai` is absent.
- `/home/akcoo/projects` is preserved as a real directory.
- Hidden home-directory configuration remained outside the deletion scope.

### WSL interoperability repair

- A full WSL restart restored `/proc/sys/fs/binfmt_misc/WSLInterop`.
- `cmd.exe /c ver` exits with status `0`.
- Windows-process interoperability passes.
- Docker Desktop's `docker-credential-desktop.exe` helper executes successfully.

### Containerised Python smoke test

- A disposable project under `/home/akcoo/projects/career-os-docker-smoke-test` built from `python:3.12.13-slim-bookworm`.
- Python ran from `/usr/local/bin/python` in `/app` as non-root UID `10001`.
- Application output reported `container_test=PASS`.
- The named test container was removed automatically.
- The test image and directory were then removed exactly.
- No project dependency was installed globally into Ubuntu.

## Step 3.5 Git result

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Global author identity is `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication uses a passphrase-protected Ed25519 key.
- GitHub authentication and repository access passed.
- Approved Git defaults are configured:
  - `init.defaultBranch=main`
  - `core.autocrlf=input`
  - `fetch.prune=true`
  - `pull.ff=only`
  - `push.autoSetupRemote=true`
- The SSH agent is session-local.

## GitHub branch-management result

- Twenty-one obsolete merged setup branches were deleted after exact allowlist and `main` preservation checks.
- **Automatically delete head branches** is enabled.
- Setup workflow now uses one `setup/step-X` branch for all substeps of top-level Step X, followed by one final pull request.

## Development environment target

- Host: Windows
- Primary source workspace: WSL 2 with Ubuntu
- Project root: `/home/akcoo/projects`
- Runtime and dependency isolation: Docker Desktop through its WSL 2 backend
- Editor target: Windows VS Code connected to WSL and, where justified, a Dev Container
- Project dependencies must not be installed globally into Ubuntu's system Python.
- Do not install a second Docker Engine directly inside Ubuntu.

## Remaining Step 3 sequence

1. **Step 3.7:** confirm the visible Dev Container indicator and Explorer marker file, then clean up only the disposable Dev Container resources and close the substep.
2. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
3. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.8 remains unauthorised.

## Immediate blocker

The exact visible Dev Container indicator text and Explorer confirmation for `devcontainer-terminal-check.txt` have not yet been reported.

## Next action

Return the exact visible Dev Container indicator text and confirm whether `devcontainer-terminal-check.txt` appears in Explorer. Preserve the test folder, Dev Container, image, and configuration until review.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.