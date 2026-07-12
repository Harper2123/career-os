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

The first Step 3.7 action is a read-only inspection of the Windows VS Code client, WSL command bridge, installed WSL and Dev Containers extensions, existing VS Code Server state, Windows executable interoperability, Docker connectivity, and the empty Linux project root.

Do not install or update extensions, run `code .`, create a project, create `.devcontainer` configuration, or begin Step 3.8 until the inspection output is reviewed.

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

## Step 3.7 inspection scope

Verify without changing the machine:

1. Windows VS Code executable path and version;
2. `code` bridge path and version from Ubuntu;
3. presence and versions of the WSL and Dev Containers extensions;
4. existing VS Code Server directories without deleting or reinstalling them;
5. Windows executable interoperability from Ubuntu;
6. Docker client/server connectivity;
7. `/home/akcoo/projects` path, filesystem, ownership, and emptiness.

Only after review may Step 3.7 open a controlled Linux-filesystem test folder through WSL and verify its integrated terminal. Dev Container connectivity remains later within Step 3.7.

## Remaining Step 3 sequence

1. **Step 3.7:** inspect and verify Windows VS Code, WSL connectivity, Linux paths, integrated terminal, and Dev Containers.
2. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
3. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.8 remains unauthorised.

## Immediate blocker

The Step 3.7 read-only VS Code and connectivity inspection has not yet been reviewed.

## Next action

Run the approved read-only Step 3.7 inspection from Ubuntu and return its complete output. Do not run `code .` yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
