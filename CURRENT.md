# Current State

_Last updated: 2026-07-12_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL as the primary personal development environment.

## Current priority

Verify the existing Ubuntu identity and base toolchain, then install or update only what the evidence shows is necessary.

## Current task

Complete Step 3.3 — Linux identity and base tools:

- reconfirm the active non-root Linux user and administrative-group membership;
- inspect package-manager state without exposing credentials or private files;
- inspect existing Git, Python, virtual-environment, compiler, network, archive, and shell tools;
- identify missing or defective minimum tools;
- update package metadata and install only the approved minimum packages after the inspection is reviewed;
- preserve the existing Linux home directory and prior projects.

Step 3.3 does not authorise creating `~/projects`, changing Git identity, creating project virtual environments, configuring VS Code extensions, reorganising prior projects, or changing WSL platform settings.

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
- Ubuntu remained running under WSL 2 after the validation.
- The earlier Windows virtualization metadata conflict is operationally resolved: WSL 2 is functioning.
- No WSL installation, repair, update, conversion, or distribution removal is required.

## Next likely task

After Step 3.3 is verified and closed, Step 3.4 will create and verify the Linux project root at `~/projects` without moving or deleting existing project directories.

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

The Step 3.3 Linux toolchain inspection has not yet been collected.

## Resume note

Run only the approved Step 3.3 inspection commands and return their complete output. Do not update packages, install packages, create `~/projects`, change Git configuration, create project virtual environments, alter shell startup files, or reorganise existing home-directory content before the inspection is reviewed.

## Next action

Complete the Step 3.3 Linux identity and base-tool inspection. Step 3.4 is not authorised.