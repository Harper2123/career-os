# Current State

_Last updated: 2026-07-12_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL as the primary personal development environment.

## Current priority

Resolve the Python-environment standard before Step 3.6 begins, then inspect obsolete local project directories before any deletion.

## Current task

Step 3.5 — Git inside WSL is complete.

Step 3.6 has not begun. Ayush does not want to use a direct `python3 -m venv .venv` workflow, so the existing WSL environment standard and setup-roadmap wording must not be executed unchanged. A replacement isolation strategy must be chosen before the standard is revised.

Ayush also requested deletion of obsolete local projects, specifically `~/quant-data-journey`. No deletion is authorised yet. The exact directory, Git state, remotes, untracked files, unpushed commits, size, and any external dependencies must be inspected first.

Do not create Python environments, install an alternative environment manager, delete or move project directories, configure VS Code, change Windows Git, alter unrelated shell settings, or run a general package upgrade until the next decision gate is explicitly approved.

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
- The Linux home directory already contains prior work and configuration and must be preserved.
- The earlier Windows virtualization metadata conflict is operationally resolved: WSL 2 is functioning.
- No WSL installation, repair, update, conversion, or distribution removal is required.

## Step 3.3 base-tool result

- The active account is non-root, uses `/bin/bash`, belongs to the `sudo` group, and has working administrative access.
- The package database audit passed and no packages are held.
- Git, OpenSSH client, CA certificates, `curl`, `wget`, `tar`, `rsync`, `build-essential`, GCC, G++, Make, Python 3, `pip`, and `venv` are installed.
- Inspected commands resolve to Linux paths under `/usr/bin` or `/bin`; Windows Git and Windows Python are not leaking into Ubuntu command resolution.
- Python is available as `python3` at `/usr/bin/python3`; the unversioned `python` command is absent and is not required by the Career OS environment standard.
- Python reports version `3.12.3`; both `python3 -m pip` and `python3 -m venv` are available.
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
- No existing home-directory project or configuration was moved, deleted, cloned, or reorganised.

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
- `clip.exe` failed from WSL with an executable-format error while copying the public key; manual public-key copy succeeded. This is not a Git blocker and should be rechecked during Step 3.7 Windows–WSL connectivity validation.

## Pending Python-environment decision

The current standard specifies project-local `venv`, but Ayush has rejected that workflow. Global `sudo pip` or unmanaged global package installation is not an acceptable replacement because it weakens reproducibility and risks damaging the system Python environment.

The replacement must still provide project isolation and reproducibility. Candidate directions are:

- Conda or Mamba environments managed natively inside WSL;
- `uv` project management, noting that it still uses isolated virtual environments internally;
- containerised development when a project genuinely requires it.

No replacement has been selected yet, so `standards/wsl-environment.md` and `plans/setup-roadmap.md` remain unchanged pending the decision.

## Pending local-project cleanup

- `~/quant-data-journey` is requested for deletion.
- The directory has not been inspected or deleted.
- The earlier inventory also observed `~/datacamp` and `~/voice-customer-support-ai`; their status is unchanged and they are not included in the deletion request.
- Deletion must follow a read-only inspection and an explicit final confirmation tied to the exact resolved path.

## Next likely task

Choose the replacement Python environment strategy. After that decision is recorded, revise the Step 3 standard and execute a read-only cleanup inspection before deleting `~/quant-data-journey`.

## Development environment target

- Host operating system: Windows.
- Primary development environment: WSL 2 with one Ubuntu distribution.
- Editor: Windows Visual Studio Code connected to WSL.
- Linux project root: `~/projects`.
- Active Linux-developed repositories must not be stored under `/mnt/c` without a specific interoperability reason.
- Environment standard: `standards/wsl-environment.md`, pending revision after the Python-environment decision.

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

- The replacement for direct `venv` usage has not been chosen.
- `~/quant-data-journey` has not been inspected for safe deletion.

## Resume note

Do not continue with the existing Step 3.6 procedure. First choose an isolated Python environment strategy, then update the governing standard. Before deleting `~/quant-data-journey`, inspect its exact path and Git state and obtain explicit final confirmation. Never expose the SSH private key or passphrase.

## Next action

Confirm the preferred replacement for `venv`. Step 3.6 remains unauthorised.
