# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` represents the last merged top-level checkpoint.
- All Step 4 substeps will be completed on this branch.
- One pull request will be created only after the full Step 4 completion condition is verified.
- Unrelated work must not be added to this branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The setup must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.1: read-only VS Code inventory.**

The Windows and WSL inventories are complete. The remaining Step 4.1 work is a narrow read-only clarification of built-in Copilot support, the exact approved AI-related settings, the WSL machine interpreter setting, and the actual stopped-server process state.

Do not alter profiles, extensions, settings, keybindings, snippets, workspace files, WSL configuration, Docker configuration, or shell configuration during Step 4.1.

## Step 4.1 Windows inventory result

### Windows client and CLI

- Windows VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- CLI capabilities listed: profiles, extension listing, extension versions, extension disabling, custom extension directory, and custom user-data directory.
- The tested CLI help did not list `--remote`.
- All VS Code windows were closed during the command-line inventory.

### Profiles and user data

- Only the `Default` profile is visible and selected.
- No profile-storage directory currently exists under the Windows VS Code user-data directory.
- `settings.json` exists.
- `keybindings.json` is absent.
- The snippets directory exists and contains zero files.
- No profile, extension, settings, or keybindings change occurred during inventory.

### Installed extensions

- Installed extension count: `36`.
- Existing capabilities include Python, Pylance, debugpy, Ruff, Jupyter, Markdown linting and preview, GitHub pull requests, Docker containers, WSL, and Dev Containers.
- Additional extension families include Python environment helpers, C and C++ tooling, CMake tooling, GitLens, themes, path helpers, CSV support, Django, Jinja, and editor decoration tools.
- GitHub Copilot and GitHub Copilot Chat do not appear in the user-installed extension list or the Installed Extensions view.

### Selected settings evidence

- `editor.formatOnSave=true`
- `git.autofetch=true`
- `git.confirmSync=false`
- `python.defaultInterpreterPath="c:\\msys64\\ucrt64\\bin\\python.exe"`
- `github.copilot.enable` exists with a complex value.
- `github.copilot.nextEditSuggestions.enabled=true`
- `editor.inlineSuggest.enabled` is not explicitly set.
- Python test settings are not explicitly set.
- The Windows and Linux default terminal profiles are not explicitly set.

### Copilot observation requiring clarification

- The bottom-right status area shows `GitHub Copilot Free`.
- Neither GitHub Copilot nor GitHub Copilot Chat appears in the user-installed extension inventory.
- Copilot-related settings remain in `settings.json`, including next-edit suggestions enabled.
- VS Code documentation for current releases states that Copilot Chat is built in, so absence from the user-installed extension list is not sufficient evidence that AI features are absent.
- The exact local built-in extension state and effective settings still require read-only verification.
- Do not assume that automatic AI completion is disabled.

### Read-only verification

- Settings hash was unchanged.
- Keybindings state was unchanged.
- Profile-directory state was unchanged.
- Extension-directory state was unchanged.
- Result: `step_4_1_windows_vscode_inventory=PASS`.

## Step 4.1 WSL inventory result

### VS Code Server

- WSL user: `akcoo`, UID/GID `1000:1000`.
- Distribution: `Ubuntu`.
- Kernel: `6.6.114.1-microsoft-standard-WSL2`.
- Architecture: `x86_64`.
- VS Code Server root: `/home/akcoo/.vscode-server`, owned by `akcoo:akcoo`.
- Server root contains `bin`, `data`, and `extensions`.
- Exactly one server installation is present under `bin`.
- Server version: `1.127.0`.
- Server commit: `4fe60c8b1cdac1c4c174f2fb180d0d758272d713`.
- Server quality: `stable`.
- The server version and commit match the Windows client.
- No CLI-style server installation exists under `.vscode-server/cli/servers`.

### Active process observation

- The original process probe reported one line.
- That line was the probe's own `grep` process, not a VS Code Server process.
- The reported count is therefore a command false positive, not evidence that the server remained active.
- A corrected `/proc`-based read-only check is required before Step 4.1 closes.

### Remote extensions

- Remote extension directory count: `32`.
- The remote registry parsed successfully and contains 32 entries.
- No remote GitHub Copilot extension directory or registry entry is present.
- Remote capabilities include Python, Pylance, debugpy, Ruff, Jupyter, GitHub pull requests, Docker tooling, Markdown tooling, C and C++ tooling, CMake tooling, and supporting editor extensions.
- Remote-only or previously retained entries include `ms-azuretools.vscode-docker`, Visual Studio IntelliCode, and IntelliCode API Usage Examples.
- These entries require design review before any removal decision.

### Remote settings

- WSL machine settings exist at `~/.vscode-server/data/Machine/settings.json`.
- WSL remote user settings are absent.
- The machine settings contain `python.defaultInterpreterPath`.
- The machine settings do not contain the inspected Copilot, inline suggestion, or Python test keys.
- The exact machine interpreter value remains to be read safely.

### Read-only verification

- Server root directories were unchanged.
- Remote extension directories were unchanged.
- `extensions.json` was unchanged.
- `.obsolete` remained absent.
- Machine settings were unchanged.
- Remote user settings remained absent.
- Results:
  - `step_4_1_wsl_server_inventory=PASS`
  - `step_4_1_wsl_remote_inventory=PASS`

## Step 4 completion condition

Step 4 is complete only when all of the following work consistently from Windows VS Code using WSL:

- Python editing and execution through the approved container workflow;
- Jupyter notebooks where justified;
- Markdown editing and preview;
- test discovery and execution;
- Git inspection and operations;
- integrated Linux terminal commands;
- Docker and Dev Container workflows;
- the minimum approved extension and profile set;
- automatic AI completion disabled by default.

This completion condition comes from `plans/setup-roadmap.md`.

## Step 4 staged sequence

1. **Step 4.1, inventory:** collect the current state without changing it.
2. **Step 4.2, design:** define the minimum profile, extension, and settings architecture from evidence.
3. **Step 4.3, Windows profile:** create or configure only the approved Windows-side profile and local extensions.
4. **Step 4.4, WSL profile:** configure only the approved WSL-side tools and remote extensions.
5. **Step 4.5, editor workflows:** validate Python, notebooks, Markdown, tests, Git, and terminal work.
6. **Step 4.6, container workflows:** validate Docker and Dev Containers through the configured editor.
7. **Step 4.7, AI completion boundary:** verify automatic AI completion remains disabled by default.
8. **Step 4.8, end-to-end test and cleanup:** run one harmless complete workflow, record evidence, and remove only disposable artifacts.
9. Review and create one Step 4 pull request only after all checks pass.

Substep details may be refined after the read-only inventory. Later substeps are not authorised merely by being listed here.

## Governing constraints

- Prefer the minimum useful configuration.
- Do not add extensions merely because they are popular.
- Do not duplicate capabilities already supplied by VS Code, WSL, Docker Desktop, or a repository-owned container.
- Keep automatic AI completion disabled by default.
- GitHub Copilot must not provide automatic code completions unless a future explicit decision changes that boundary.
- Preserve the Step 3 architecture: Windows as host, Ubuntu WSL as the primary Linux workspace, and Docker Desktop as the project runtime.
- Do not install project dependencies into Ubuntu's system Python.
- Do not begin Step 5 Git and GitHub workflow practice during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.
- Excessive VS Code customisation remains excluded from Career OS v1.

## Verified Step 3 baseline

- Ubuntu 24.04 under WSL 2 is healthy with systemd.
- Linux user `akcoo` is non-root with UID/GID `1000:1000`.
- Linux project root is `/home/akcoo/projects` on `ext4`.
- WSL Git and GitHub SSH authentication pass.
- Docker Desktop WSL integration works from Ubuntu.
- Windows VS Code previously opened a Linux project through WSL.
- WSL and Dev Containers extensions were present during Step 3 and remain present in the Windows extension inventory.
- A repository-owned Python `3.12.13` image ran directly and through a Dev Container as a non-root user.
- Host-side ownership remained correct.
- Disposable Step 3 artifacts were removed exactly.

## Immediate blocker

No technical blocker is known. Step 4.1 needs the narrow clarification checks described above before the minimum VS Code architecture can be designed.

## Next action

Run the approved read-only Windows AI-feature and WSL settings/process clarification checks. Return the complete outputs. Do not make any VS Code change yet.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
