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

**Step 3.6 — containerised Python runtime** is active.

The remaining Step 3.6 action is to retry the existing minimal Python smoke-test build after WSL interoperability was restored.

Existing test state:

- test directory: `/home/akcoo/projects/career-os-docker-smoke-test`
- files retained: `.dockerignore`, `Dockerfile`, `app.py`
- intended image: `career-os-python-smoke:step-3-6`
- image is absent because the first build failed before download;
- no test container exists.

## Step 3.6 verified state

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

The first Docker build failed because Docker Desktop's Windows credential helper could not execute from Ubuntu. Diagnosis found that the `WSLInterop` binfmt registration was absent even though interoperability was not disabled.

After quitting Docker Desktop, running `wsl --shutdown`, restarting Docker Desktop, and opening a fresh Ubuntu session:

- `/proc/sys/fs/binfmt_misc/WSLInterop` is present and enabled;
- the interpreter is `/init` with `PF` flags and `4d5a` magic;
- `cmd.exe /c ver` exits with status `0`;
- Windows process interoperability passes;
- Docker client/server connectivity still passes;
- the smoke-test directory remains intact;
- the smoke-test image remains absent.

## Step 3.5 Git result

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Global author identity is `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication uses a passphrase-protected Ed25519 key.
- GitHub authentication succeeded as `Harper2123`.
- Authenticated SSH repository access passed.
- Approved Git defaults are configured:
  - `init.defaultBranch=main`
  - `core.autocrlf=input`
  - `fetch.prune=true`
  - `pull.ff=only`
  - `push.autoSetupRemote=true`
- The SSH agent is session-local.

## GitHub branch-management result

- Twenty-one obsolete merged setup branches were deleted after exact allowlist and `main` preservation checks.
- The cleanup verification reported only `main` before the new Step 3 working branch was created.
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

1. **Step 3.6:** build, run, verify, and clean up the disposable Python container test.
2. **Step 3.7:** verify Windows VS Code, WSL connectivity, Linux paths, integrated terminal, and Dev Containers; recheck Windows executable interoperability.
3. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
4. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.7 remains unauthorised until Step 3.6 closes.

## Immediate blocker

The existing Docker smoke-test image has not yet been built and run after the interoperability repair.

## Next action

Retry the build from `/home/akcoo/projects/career-os-docker-smoke-test`, run the image as a non-root user, verify container output and automatic container removal, then remove only the explicitly disposable image and test directory after review.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
