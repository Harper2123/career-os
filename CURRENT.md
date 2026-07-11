# Current State

_Last updated: 2026-07-11_

## Operating mode

**Career OS setup mode**

Steps 1 and 2 are complete. Step 3 is active: prepare WSL as the primary personal development environment.

## Current priority

Inspect the existing Windows and WSL state before making any installation, repair, conversion, or deletion decision.

## Current task

Complete Step 3.1 — environment inventory:

- verify the Windows version and build;
- inspect WSL status and component version;
- list installed Linux distributions and their WSL versions;
- confirm whether hardware virtualization is available;
- inspect existing Git, Python, and VS Code command availability;
- preserve any existing WSL files before later changes.

No installation or destructive WSL command is authorised until the inventory has been reviewed.

## Next likely task

Choose the minimum Step 3.2 action based on evidence: retain the healthy environment, update it, install a distribution, convert a distribution to WSL 2, or repair a specific defect.

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

The Step 3.1 environment inventory has not yet been collected.

## Resume note

Run only the approved read-only Windows and WSL diagnostic commands, then return their complete output for review.

Do not run `wsl --install`, `wsl --update`, `wsl --set-version`, `wsl --unregister`, package installation commands, or filesystem migration commands before the inventory is reviewed.

## Next action

Complete the Step 3.1 environment inventory and report the output. Step 3.2 is not yet authorised.
