# Current State

_Last updated: 2026-07-12_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL as the primary personal development environment.

## Current priority

Finish Step 3.5 by creating a passphrase-protected Ed25519 SSH key inside WSL, registering its public key with GitHub, applying the minimum approved Git defaults, and verifying authenticated SSH access.

## Current task

Step 3.5 — Git inside WSL is active.

The inspection and authentication-method decision are complete. The next authorised actions are:

- retain the existing commit-author identity `Ayush Kumar <akcoolkmr@gmail.com>`;
- generate a passphrase-protected Ed25519 key pair inside `~/.ssh`;
- add only the public key to Ayush's GitHub account as an authentication key;
- add the private key to a session-local WSL SSH agent;
- configure the approved minimum Git defaults inside WSL;
- verify GitHub SSH authentication and read-only access to `Harper2123/career-os`.

Do not expose the private key or its passphrase, use plaintext credential storage, change Windows Git, move or clone repositories, push commits, create Python virtual environments, configure VS Code, modify unrelated shell settings, or run a general package upgrade.

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

## Step 3.5 Git inspection and decision result

- WSL Git is `/usr/bin/git`, resolves to the Linux binary, and reports version `2.43.0`.
- The existing global Git configuration file is `/home/akcoo/.gitconfig`, owned by the Linux user with mode `644`.
- The existing global author identity is `Ayush Kumar <akcoolkmr@gmail.com>` and will be retained.
- `init.defaultBranch`, line-ending policy, pull policy, pruning, push defaults, signing, and credential-helper settings were unset at inspection time.
- No Git identity or configuration environment-variable overrides were found.
- No Git URL rewrite rules were found.
- No plaintext Git credential files or `.netrc` file were found.
- No Git credential helper is installed inside WSL.
- `~/.ssh` has secure directory permissions (`700`) and contained only `known_hosts` at inspection time; no private or public SSH key files were present.
- No SSH agent was running and no identities were loaded.
- Read-only HTTPS access to `Harper2123/career-os` succeeded.
- Ayush explicitly selected WSL-native SSH authentication.
- The approved implementation is a passphrase-protected Ed25519 key pair created inside WSL, with only its public key registered on GitHub.
- Authenticated SSH access has not yet been configured or verified.

## Next likely task

After Step 3.5 is verified and closed, Step 3.6 will validate Python project-local virtual environments under `~/projects` without installing project packages globally.

## Development environment target

- Host operating system: Windows.
- Primary development environment: WSL 2 with one Ubuntu distribution.
- Editor: Windows Visual Studio Code connected to WSL.
- Linux project root: `~/projects`.
- Active Linux-developed repositories must not be stored under `/mnt/c` without a specific interoperability reason.
- Environment standard: `standards/wsl-environment.md`.

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

The WSL SSH key has not yet been generated or registered with GitHub. Authenticated SSH access and the minimum Git defaults remain unverified.

## Resume note

Create and register only the approved WSL-native authentication key, then apply and verify the minimum Git defaults. Do not expose private-key contents or passphrases, add the key as a signing key, change Windows Git, clone or move repositories, push commits, create virtual environments, configure VS Code, or run a general package upgrade.

## Next action

Generate the WSL Ed25519 SSH key, add its public key to GitHub as an authentication key, and return the approved verification output. Step 3.6 is not authorised.
