# Current State

_Last updated: 2026-07-12_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL and Docker as the primary development environment.

## Current priority

Complete Step 3.6 by removing the three explicitly authorised obsolete visible project directories, revising the environment standard for containerised Python, and verifying Docker Desktop's WSL integration from Ubuntu.

## Current task

Step 3.6 — containerised Python runtime is active.

Ayush explicitly authorised deletion of exactly these directories and stated that they are safe to delete:

- `/home/akcoo/datacamp`
- `/home/akcoo/quant-data-journey`
- `/home/akcoo/voice-customer-support-ai`

`/home/akcoo/projects` must remain. Hidden files and directories under `/home/akcoo`, including SSH material, Git configuration, cloud configuration, and VS Code server files, are outside the deletion scope.

The deletion procedure must use exact path guards and must not use a wildcard over the home directory. After cleanup, inspect Docker availability and Docker Desktop's Ubuntu integration before building any image.

Do not install Docker Engine directly inside Ubuntu, create `venv` or Conda environments, configure VS Code, clone repositories, alter unrelated shell settings, or run a general package upgrade during this phase.

## Step 3.1 inventory result

- Windows is 64-bit and supports the installed WSL command set.
- The Store-delivered WSL component is installed and reports version `2.7.3.0`.
- The default WSL version is `2`.
- `Ubuntu` is installed, is the default distribution, and is configured for WSL 2.
- `docker-desktop` is present under WSL 2 and is not treated as a personal development distribution.
- Windows Visual Studio Code, Git, Miniforge Python, and the Python launcher are available.
- No evidence supports reinstalling WSL, installing another Ubuntu distribution, converting the existing distribution, or unregistering anything.

## Step 3.2 platform result

- The existing Ubuntu distribution starts and executes Linux commands successfully.
- The distribution is Ubuntu `24.04.2 LTS`.
- The kernel is `6.6.114.1-microsoft-standard-WSL2`.
- `systemd` is running as process 1.
- The default Linux account is a non-root user with UID and GID `1000`.
- The user home directory is under `/home`, is owned by the Linux user, and is stored on the Linux `ext4` filesystem.
- The earlier Windows virtualization metadata conflict is operationally resolved: WSL 2 is functioning.
- No WSL installation, repair, update, conversion, or distribution removal is required.

## Step 3.3 base-tool result

- The active account is non-root, uses `/bin/bash`, belongs to the `sudo` group, and has working administrative access.
- The package database audit passed and no packages are held.
- Git, OpenSSH client, CA certificates, `curl`, `wget`, `tar`, `rsync`, `build-essential`, GCC, G++, Make, Python 3, `pip`, and `venv` are installed.
- Inspected commands resolve to Linux paths under `/usr/bin` or `/bin`; Windows Git and Windows Python are not leaking into Ubuntu command resolution.
- Python is available as `python3` at `/usr/bin/python3` and reports version `3.12.3`.
- Direct project `venv`, Conda, and Miniforge environments are not the selected Career OS workflow.
- Ubuntu archive and GitHub DNS and HTTPS checks passed.
- `zip` and `unzip` are installed and the package database audit passed.
- No general package upgrade was performed. The reported `240` upgradable packages are deferred and are not a Step 3 blocker.

## Step 3.4 project-filesystem result

- `~/projects` exists as `/home/akcoo/projects`.
- It is a real directory, owned by the active non-root Linux user, with mode `755`.
- It resides on the Linux `ext4` filesystem and is not under `/mnt`.
- It contained zero entries when verified and is the retained root for future repositories.

## Step 3.5 Git result

- WSL Git is `/usr/bin/git`, version `2.43.0`.
- The retained global author identity is `Ayush Kumar <akcoolkmr@gmail.com>`.
- WSL-native SSH authentication is configured with a passphrase-protected Ed25519 key.
- GitHub authentication succeeded as `Harper2123`.
- Authenticated SSH read access to `career-os` passed.
- The approved Git defaults are configured:
  - `init.defaultBranch=main`
  - `core.autocrlf=input`
  - `fetch.prune=true`
  - `pull.ff=only`
  - `push.autoSetupRemote=true`
- The SSH agent is session-local.
- `clip.exe` failed from WSL with an executable-format error and should be rechecked during Windows–WSL connectivity validation.

## Step 3.6 decisions

- Source repositories remain under `~/projects` in the WSL Linux filesystem.
- Docker Desktop's WSL 2 backend is the default project runtime and dependency-isolation layer.
- Ubuntu must receive Docker Desktop WSL integration so Docker commands are available from the Ubuntu terminal.
- Python versions, system dependencies, and Python packages belong in project-owned container definitions.
- Docker Compose is added only for justified multi-service workflows.
- VS Code Dev Containers may reuse the same Dockerfile or Compose configuration later.
- No project packages are installed globally into Ubuntu's system Python.
- A second Docker Engine must not be installed directly inside Ubuntu while Docker Desktop integration is the selected architecture.
- The WSL environment standard and setup roadmap were revised on the active Step 3.6 branch to replace the superseded `venv` workflow.

## Current cleanup state

Deletion is authorised but not yet verified as completed.

The exact deletion targets are:

- `~/datacamp`
- `~/quant-data-journey`
- `~/voice-customer-support-ai`

The retained visible directory is:

- `~/projects`

All hidden home-directory entries remain protected from this cleanup.

## Next likely task

After cleanup verification, inspect:

- the Docker CLI path and version inside Ubuntu;
- the active Docker context;
- client/server connectivity;
- Docker Desktop engine details;
- Docker Compose availability.

If integration passes, create a minimal disposable Python container test under `~/projects` without installing packages globally.

## Development environment target

- Host operating system: Windows.
- Primary source workspace: WSL 2 with Ubuntu.
- Project runtime and dependency isolation: Docker Desktop through its WSL 2 backend.
- Editor: Windows Visual Studio Code connected to WSL and, where justified, a project Dev Container.
- Linux project root: `~/projects`.
- Active Linux-developed repositories must not be stored under `/mnt/c` without a specific interoperability reason.
- Environment standard: `standards/wsl-environment.md`, revised on the active Step 3.6 branch.

## ChatGPT workspace status

- Active Project: `Career OS`.
- Active setup conversation: `00 — Career OS Architecture & Setup`.
- Career OS uses default memory, while GitHub remains authoritative.
- Workspace rules are maintained in `standards/chatgpt-workspace.md`.

## MScFE status

- Completed courses: Financial Markets, Financial Data, and Financial Econometrics.
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation.
- Raw WQU materials remain private.

## Personal engineering status

- No active flagship project.
- Previous general AI roadmap and Telco churn service were intentionally deleted.
- Project selection will occur only after the selection framework is defined and enough financial-domain exposure exists.

## Capacity rule

During an active MScFE course, unrelated personal AI engineering is capped at approximately 3–4 hours per week. During a break, the expected range is approximately 6–10 hours per week, while preserving recovery.

## Immediate blockers

- The three authorised deletion targets have not yet been removed and verified.
- Docker Desktop's Ubuntu integration and containerised Python execution have not yet been verified.

## Resume note

Run only the exact guarded cleanup and Docker inspection commands for Step 3.6. Preserve `~/projects` and all hidden home-directory configuration. Never expose the SSH private key or passphrase. Do not install a second Docker Engine inside Ubuntu.

## Next action

Delete the three explicitly authorised obsolete directories with exact path guards, verify the home directory, then run the Docker integration inspection. Step 3.7 is not authorised.