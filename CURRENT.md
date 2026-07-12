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

**Step 3.7 — VS Code connectivity is active.**

The VS Code and connectivity inspection passed. The next Step 3.7 action is to create one controlled disposable folder under `/home/akcoo/projects`, open it through the WSL connection, and verify that the VS Code status indicator, integrated terminal, user identity, working directory, kernel, filesystem, and file ownership are Linux-side.

Do not install or update extensions, create Dev Container configuration, or begin Step 3.8 until the WSL-folder test is reviewed.

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
- `/home/akcoo/projects` resolves correctly, resides on `ext4`, is owned by `akcoo:akcoo`, has mode `755`, and contains zero entries.

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
- `projects` is the only visible home-directory entry.
- Hidden home-directory configuration remained outside the deletion scope.

### WSL interoperability repair

- A full WSL restart restored `/proc/sys/fs/binfmt_misc/WSLInterop`.
- `cmd.exe /c ver` exits with status `0`.
- Windows process interoperability passes.
- Docker Desktop's `docker-credential-desktop.exe` helper executes successfully.

### Containerised Python smoke test

- A disposable project under `/home/akcoo/projects/career-os-docker-smoke-test` built from `python:3.12.13-slim-bookworm`.
- Python ran from `/usr/local/bin/python` in `/app` as non-root UID `10001`.
- Application output reported `container_test=PASS`.
- The named test container was removed automatically.
- The test image and directory were then removed exactly.
- `/home/akcoo/projects` was verified empty afterward.
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

1. **Step 3.7:** open and verify a controlled Linux folder through WSL, then verify Dev Containers connectivity.
2. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
3. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.8 remains unauthorised.

## Immediate blocker

The controlled WSL-folder opening and integrated-terminal verification have not yet been completed.

## Next action

Create one disposable folder under `/home/akcoo/projects`, open it with Windows VS Code through WSL, verify the remote status indicator and Linux integrated terminal, and return the terminal output plus the observed remote status text. Do not create `.devcontainer` configuration yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
