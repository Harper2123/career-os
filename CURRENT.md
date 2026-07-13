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

**Step 3.7 — VS Code connectivity is verified; exact cleanup is authorised next.**

The WSL-folder and Dev Container checks passed. Cleanup inspection identified one stopped disposable container, one project-specific generated image, one shared `vscode` volume, and one disposable test folder.

The next action is to remove only the identified stopped container, the identified project-specific generated image, and the identified test folder. Preserve the shared `vscode` volume, base-image layers, Docker cache, VS Code Server, extensions, and all unrelated Docker resources.

Do not begin Step 3.8 until cleanup output is reviewed and Step 3.7 is formally closed.

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
- `devcontainer-terminal-check.txt` remained owned by `akcoo:akcoo` on Ubuntu.
- Dev Container result: `step_3_7_devcontainer_terminal_verification=PASS`.
- Host ownership result: `step_3_7_host_ownership_verification=PASS`.

## Step 3.7 cleanup inspection

### Disposable test folder

Exact path:

`/home/akcoo/projects/career-os-vscode-wsl-check`

Verified contents:

- `.devcontainer/devcontainer.json`
- `README.md`
- `devcontainer-terminal-check.txt`
- `vscode-terminal-check.txt`

### Matching container

- Exactly one container matched the test-folder mount.
- Container ID: `4e1ca1a45fa59baf2a1d5f468760001e80864df3059e3f1930b9ac807f5f1aa1`
- Container name: `jolly_hodgkin`
- Status: `exited`
- Running: `false`
- Exit code: `0`
- The container is safe to remove exactly by ID.

### Generated image

- Image ID: `sha256:5059f6d7370947f51aeb2d1aabf17b703636839bd192dddc4085adf9c6775b41`
- Project-specific tag: `vsc-career-os-vscode-wsl-check-f4856169806bc0c1c53fc5c02ee74bc09ac1b452c5c2d92328d5f79172b04396-uid:latest`
- Size: `620684183` bytes.
- Operating system and architecture: `linux/amd64`.
- Exactly one container references this image, and it is the identified disposable container.
- The generated image is safe to remove after the container is removed.

### Mounts and preserved resources

The container had:

1. the disposable project-folder bind mount;
2. a transient Docker Desktop Wayland socket bind mount;
3. the named volume `vscode` mounted at `/vscode`.

The `vscode` named volume is shared infrastructure and must be preserved. Do not remove it. Do not run any prune command. Do not explicitly remove base images or cache layers.

## Step 3.6 completion result

- Docker Desktop WSL integration is operational.
- Docker client and server both report `29.4.3`; Compose reports `v5.1.3`.
- No competing native Ubuntu Docker Engine packages were found.
- A disposable Python `3.12.13` image built and ran under Docker as a non-root user.
- No project dependency was installed globally into Ubuntu.

## Git and branch state

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- Author identity: `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication and GitHub repository access pass.
- **Automatically delete head branches** is enabled.
- Setup workflow uses one `setup/step-X` branch per top-level step, followed by one final pull request.

## Remaining Step 3 sequence

1. **Step 3.7:** remove only the exact disposable container, generated image, and test folder; verify cleanup; close the substep.
2. **Step 3.8:** complete one harmless end-to-end environment test and close Step 3.
3. Create one pull request from `setup/step-3` to `main`, review, merge, and verify automatic branch deletion.

Step 3.8 remains unauthorised.

## Immediate blocker

The exact Step 3.7 cleanup has not yet been executed and verified.

## Next action

Remove only the identified stopped container, identified generated image, and exact test folder using guarded commands. Preserve the `vscode` volume and all unrelated resources. Return the full cleanup and verification output.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 — Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3–4 hours per week.
