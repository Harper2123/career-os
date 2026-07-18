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

**Step 4.1 is complete. Step 4.2 awaits explicit approval.**

The Windows client, profiles, installed extensions, approved settings, built-in Copilot component, WSL VS Code Server, remote extensions, WSL machine settings, and stopped-server process state were inventoried without changing configuration.

Do not design or apply the minimum profile, extension, or settings architecture until the exact instruction `Proceed to Step 4.2` is given.

## Step 4.1 Windows inventory result

### Windows client and CLI

- Windows VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- CLI capabilities listed: profiles, extension listing, extension versions, extension disabling, custom extension directory, and custom user-data directory.
- The tested CLI help did not list `--remote`.
- All VS Code windows were closed during command-line inventory and clarification.

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
- Extension overlap and retained tooling will be evaluated during Step 4.2 before any removal decision.

### Selected non-AI settings evidence

- `editor.formatOnSave=true`
- `git.autofetch=true`
- `git.confirmSync=false`
- `python.defaultInterpreterPath="c:\\msys64\\ucrt64\\bin\\python.exe"`
- Python test settings are not explicitly set.
- The Windows and Linux default terminal profiles are not explicitly set.

### Built-in Copilot and AI settings result

- The bottom-right status area shows `GitHub Copilot Free`.
- `code --locate-extension github.copilot` returned no location.
- `code --locate-extension github.copilot-chat` located a built-in component under the versioned VS Code installation directory.
- Located package ID: `GitHub.copilot-chat`.
- Located package version: `0.57.0`.
- The versioned installation layout explains why the earlier unversioned `resources\app\extensions` assumption failed.
- `chat.disableAIFeatures` is not set.
- `chat.experimental.statusIndicator.enabled` is not set.
- `editor.inlineSuggest.enabled` is not set.
- `github.copilot.editor.enableAutoCompletions` is not set.
- `github.copilot.enable` is configured as `{ "*": false, "plaintext": true, "markdown": false, "scminput": false, "python": true }`.
- `github.copilot.nextEditSuggestions.enabled=true`.
- Copilot is therefore explicitly enabled for Python and plaintext while next-edit suggestions are enabled.
- The required automatic AI completion boundary is not currently satisfied and must be corrected and verified in later authorised Step 4 work.

### Read-only verification

- Settings hash was unchanged.
- Keybindings state was unchanged.
- Profile-directory state was unchanged.
- User extension-directory state was unchanged.
- Results:
  - `step_4_1_windows_vscode_inventory=PASS`
  - `step_4_1_windows_clarification=PASS`
- The first Windows clarification command stopped on an incorrect path assumption and made no intended write.

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

### Active process result

- The original process probe reported its own `grep` process and was a false positive.
- A corrected `/proc`-based check found zero actual VS Code Server processes.
- Result: `actual_vscode_server_process_count=0`.
- Result: `actual_server_process_state=STOPPED`.

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
- `python.defaultInterpreterPath="/bin/python3"`.
- Python test, inline suggestion, Copilot, and AI-disable settings are not explicitly set in WSL machine settings.
- The WSL machine settings parsed successfully and remained unchanged.

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
  - `step_4_1_wsl_clarification=PASS`

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

1. **Step 4.1, inventory: complete.**
2. **Step 4.2, design:** define the minimum profile, extension, and settings architecture from evidence.
3. **Step 4.3, Windows profile:** create or configure only the approved Windows-side profile and local extensions.
4. **Step 4.4, WSL profile:** configure only the approved WSL-side tools and remote extensions.
5. **Step 4.5, editor workflows:** validate Python, notebooks, Markdown, tests, Git, and terminal work.
6. **Step 4.6, container workflows:** validate Docker and Dev Containers through the configured editor.
7. **Step 4.7, AI completion boundary:** verify automatic AI completion remains disabled by default.
8. **Step 4.8, end-to-end test and cleanup:** run one harmless complete workflow, record evidence, and remove only disposable artifacts.
9. Review and create one Step 4 pull request only after all checks pass.

Later substeps are not authorised merely by being listed here.

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
- WSL and Dev Containers extensions remain present in the Windows extension inventory.
- A repository-owned Python `3.12.13` image ran directly and through a Dev Container as a non-root user.
- Host-side ownership remained correct.
- Disposable Step 3 artifacts were removed exactly.

## Immediate blocker

Step 4.2 requires explicit approval. There is no unresolved Step 4.1 technical blocker.

## Next action

Wait for the exact instruction `Proceed to Step 4.2` before designing the minimum VS Code profile, extension, and settings architecture.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
