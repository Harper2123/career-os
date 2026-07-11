# Current State

_Last updated: 2026-07-12_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL as the primary personal development environment.

## Current priority

Revise Step 3 around containerised Python development, then inspect the three obsolete visible project directories before any deletion.

## Current task

Step 3.5 — Git inside WSL is complete.

Step 3.6 has not begun. Ayush has selected Docker rather than direct `venv`, Conda, or Miniforge as the default project isolation and runtime strategy.

The visible home-directory cleanup scope is now exactly:

- `/home/akcoo/datacamp`
- `/home/akcoo/quant-data-journey`
- `/home/akcoo/voice-customer-support-ai`

`/home/akcoo/projects` must remain. Hidden files and directories under `/home/akcoo` are outside the deletion scope and must not be removed.

No deletion is authorised yet. Each exact directory must first be inspected for its resolved path, Git repositories including nested repositories, remotes, modified or untracked files, ignored files, local branches, commits not represented on remotes, repository size, and symlinks. Git synchronisation alone is not proof that all local content is recoverable.

Do not create Python environments, install another environment manager, delete or move project directories, configure VS Code, change Windows Git, alter unrelated shell settings, or run a general package upgrade until Step 3.6 is explicitly authorised.

## Step 3.1 inventory result

- Windows is 64-bit and supports the installed WSL command set.
- The Store-delivered WSL component is installed and reports version `2.7.3.0`.
- The default WSL version is `2`.
- `Ubuntu` is installed, is the default distribution, and is configured for WSL 2.
- `docker-desktop` is also present under WSL 2 and is not treated as a personal development distribution.
- Windows Visual Studio Code, Git, Miniforge Python, and the Python launcher are available.
- No evidence supports reinstalling WSL, installing another Ubuntu distribution, converting the existing distribution, or unregistering anything.

## Step 3.2 platform result

- The existing Ubuntu distribution starts and executes Linux commands successfully.
- The distribution is Ubuntu `24.04.2 LTS`.
- The kernel is `6.6.114.1-microsoft-standard-WSL2`.
- `systemd` is running as process 1.
- The default Linux account is a non-root user with UID and GID `1000`.
- The user home directory is under `/home`, is owned by the Linux user, and is stored on the Linux `ext4` filesystem.
- The Linux home directory already contains prior work and configuration and must be preserved except for separately inspected and explicitly confirmed obsolete project directories.
- The earlier Windows virtualization metadata conflict is operationally resolved: WSL 2 is functioning.
- No WSL installation, repair, update, conversion, or distribution removal is required.

## Step 3.3 base-tool result

- The active account is non-root, uses `/bin/bash`, belongs to the `sudo` group, and has working administrative access.
- The package database audit passed and no packages are held.
- Git, OpenSSH client, CA certificates, `curl`, `wget`, `tar`, `rsync`, `build-essential`, GCC, G++, Make, Python 3, `pip`, and `venv` are installed.
- Inspected commands resolve to Linux paths under `/usr/bin` or `/bin`; Windows Git and Windows Python are not leaking into Ubuntu command resolution.
- Python is available as `python3` at `/usr/bin/python3`; the unversioned `python` command is absent.
- Python reports version `3.12.3`; both `python3 -m pip` and `python3 -m venv` are available, but direct project `venv` usage is no longer the selected Career OS workflow.
- Ubuntu archive and GitHub DNS and HTTPS checks passed.
- Ubuntu package metadata refreshed successfully without repository, DNS, signature, or release-file errors.
- `zip` version `3.0-13ubuntu0.2` and `unzip` version `6.0-28ubuntu4.1` were installed as the only missing minimum tools.
- Both commands resolve to `/usr/bin`, and the post-installation package database audit passed.
- No general package upgrade was performed. The reported `240` upgradable packages are deferred and are not a Step 3 blocker.

## Step 3.4 project-filesystem result

- `~/projects` was created without `sudo` as `/home/akcoo/projects`.
- The path is a real directory rather than a symbolic link.
- The directory is owned by the active non-root Linux user with UID and GID `1000`.
- Permissions are `drwxr-xr-x` with mode `755`.
- The directory resides on the Linux `ext4` filesystem and is not under `/mnt`.
- The directory contains zero entries and is ready for future Linux-developed repositories.
- No existing home-directory project or configuration was moved, deleted, cloned, or reorganised during Step 3.4.

## Step 3.5 Git result

- WSL Git is `/usr/bin/git`, resolves to the Linux binary, and reports version `2.43.0`.
- The global Git configuration file is `/home/akcoo/.gitconfig`, owned by the Linux user.
- The retained global author identity is `Ayush Kumar <akcoolkmr@gmail.com>`.
- No Git identity or configuration environment-variable overrides, URL rewrite rules, plaintext credential files, `.netrc`, or credential helper were found.
- WSL-native SSH authentication was selected.
- A passphrase-protected Ed25519 key pair was created inside `~/.ssh`.
- The private key has mode `600`; the public key has mode `644`; the `~/.ssh` directory retains mode `700`.
- Only the public key was registered with GitHub as an authentication key.
- A session-local WSL SSH agent loaded the key successfully.
- `ssh -T git@github.com` authenticated as `Harper2123`; GitHub's expected no-shell exit status was observed.
- Authenticated SSH read access to `git@github.com:Harper2123/career-os.git` passed.
- The approved WSL Git defaults are configured:
  - `init.defaultBranch=main`
  - `core.autocrlf=input`
  - `fetch.prune=true`
  - `pull.ff=only`
  - `push.autoSetupRemote=true`
- No repository was cloned, moved, or pushed during Step 3.5.
- The SSH agent is intentionally session-local. A new shell may require starting `ssh-agent` and running `ssh-add ~/.ssh/id_ed25519` again until a later workflow explicitly addresses persistence.
- `clip.exe` failed from WSL with an executable-format error while copying the public key; manual public-key copy succeeded. This is not a Git blocker and should be rechecked during Windows–WSL connectivity validation.

## Containerised Python decision

Ayush selected Docker as the default isolation and runtime strategy instead of direct `venv`, Conda, or Miniforge environments.

The intended architecture is:

- source repositories remain under `~/projects` on the WSL Linux filesystem;
- Docker Desktop uses its WSL 2 backend;
- Ubuntu receives Docker Desktop WSL integration so Docker commands are available from the Ubuntu terminal;
- Python versions, system dependencies, and Python packages are defined per repository in a `Dockerfile`, with Docker Compose added only when multiple services or durable development services are justified;
- VS Code Dev Containers may later use the same Dockerfile or Compose configuration for the full editor environment;
- no project packages are installed globally into Ubuntu's system Python;
- container definitions, dependency lock files, tests, and run instructions belong in each project repository.

Docker is a deliberate higher-overhead choice. It provides stronger environmental reproducibility and deployment alignment, but image builds, storage use, GPU integration, file ownership, secrets, and container lifecycle must be managed explicitly. The system must not add containers to trivial non-Python work merely for appearance.

`standards/wsl-environment.md` and `plans/setup-roadmap.md` still contain the earlier `venv` wording and require a controlled revision during the approved Step 3.6 work.

## Pending local-project cleanup

The following visible directories are requested for deletion after inspection and final confirmation:

- `~/datacamp`, including the observed nested `datacamp-code-alongs` content;
- `~/quant-data-journey`;
- `~/voice-customer-support-ai`.

`~/projects` is explicitly retained. Hidden home-directory entries, SSH material, Git configuration, cloud configuration, VS Code server files, and unrelated user configuration are outside the cleanup scope.

The directories have not been deleted. A read-only inspection must identify nested Git repositories, remotes, working-tree changes, untracked and ignored files, local-only commits, sizes, and symlinks before an exact deletion confirmation is requested.

## Next likely task

Under Step 3.6, first perform a read-only cleanup inspection of the three exact directories. After the inspection is reviewed, obtain explicit final confirmation for deletion. Then revise the WSL standard and setup roadmap for containerised Python and verify Docker Desktop's WSL integration and a minimal containerised Python execution under `~/projects`.

## Development environment target

- Host operating system: Windows.
- Primary source workspace: WSL 2 with Ubuntu.
- Project runtime and dependency isolation: Docker containers through Docker Desktop's WSL 2 backend.
- Editor: Windows Visual Studio Code connected to WSL and, where justified, a project Dev Container.
- Linux project root: `~/projects`.
- Active Linux-developed repositories must not be stored under `/mnt/c` without a specific interoperability reason.
- Environment standard: `standards/wsl-environment.md`, pending controlled revision in Step 3.6.

## ChatGPT workspace status

- Active Project: `Career OS`.
- Active setup conversation: `00 — Career OS Architecture & Setup`.
- Career OS uses default memory, while GitHub remains authoritative.
- Workspace rules are maintained in `standards/chatgpt-workspace.md`.
- Future MScFE and flagship-project Projects will be created only when real work requires them.
- A separate Public Presence Project is not part of v1.
- The Step 2.3 clean-conversation context test passed on 2026-07-11.

## MScFE status

- Completed courses: Financial Markets, Financial Data, and Financial Econometrics.
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation.
- Module materials will be processed only after release and sharing.
- Each module will begin with a material inventory, capability brief, and question map before purposeful reading.

## Personal engineering status

- No active flagship project.
- Previous general AI roadmap and Telco churn service were intentionally deleted.
- Project selection will occur only after the project-selection framework is defined and enough financial-domain exposure exists.

## Capacity rule

During an active MScFE course, unrelated personal AI engineering is capped at approximately 3–4 hours per week. During a break, the expected range is approximately 6–10 hours per week, while preserving recovery.

## Immediate blockers

- Step 3.6 has not been explicitly authorised.
- The three deletion targets have not received the required read-only safety inspection.
- The WSL standard and setup roadmap still contain the superseded `venv` wording.
- Docker Desktop's Ubuntu integration and containerised Python execution have not yet been verified.

## Resume note

Do not delete anything yet. Preserve `~/projects` and all hidden home-directory configuration. Begin Step 3.6 only after explicit approval, starting with read-only inspection of exactly `~/datacamp`, `~/quant-data-journey`, and `~/voice-customer-support-ai`. Never expose the SSH private key or passphrase.

## Next action

Await `Proceed to Step 3.6` before running the cleanup inspection or changing the environment standard.
