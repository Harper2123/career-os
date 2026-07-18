# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` represents the last merged top-level checkpoint.
- All Step 4 work remains on this branch.
- One pull request will be created only after the full Step 4 completion condition is verified.
- Unrelated work must not be added to this branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The setup must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.4 is active.**

Steps 4.4a, 4.4b, and 4.4c are complete. The current subtask is **Step 4.4d: verify the integrated Linux terminal, WSL settings, and interpreter boundary from the approved open WSL workspace**.

During Step 4.4d:

- keep the approved WSL window open with `Career OS Engineering` active;
- use only the integrated terminal and read-only inspection commands;
- do not install packages or Python dependencies;
- do not change WSL machine settings, profile settings, Settings Sync, extension state, interpreters, tests, keybindings, terminal profiles, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 4.5 or Step 5.

## Step 4.3 completion checkpoint

The final Windows-side checkpoint passed:

```text
step_4_3e_windows_profile_checkpoint=PASS
```

Verified Windows profile state:

- profile: `Career OS Engineering`;
- created from Empty Profile;
- persistent profile directory ID: `-639a60a5`;
- Career OS extension membership: exactly `15` approved entries;
- Default extension membership: `36`;
- no Windows Python interpreter is configured in the Career OS profile;
- no global test framework, terminal profile, Ruff rules, or keybindings are configured;
- automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions are disabled across Default and Career OS profiles;
- `chat.disableAIFeatures` remains unset so deliberate manual chat is preserved;
- Settings Sync was not changed.

Current Windows settings hashes:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

## Step 4.4 objective

Open a harmless WSL workspace with `Career OS Engineering` and verify:

- profile continuity in a WSL window;
- correct local and remote extension placement;
- active remote extension scope;
- Linux terminal identity and working directory;
- WSL remote settings;
- interpreter boundaries;
- absence of unrelated active remote extension families;
- preservation of the Step 4.3 Windows checkpoint;
- no manual deletion of remote extension directories.

The governing standard is `standards/vscode-environment.md`.

## Step 4.4 staged sequence

1. **Step 4.4a: complete.** Read-only WSL workspace-candidate and remote-state preflight, including corrected recovery verification.
2. **Step 4.4b: complete.** Create the approved harmless folder, open it through the Windows WSL workflow with `Career OS Engineering`, and confirm profile and remote-context continuity.
3. **Step 4.4c: complete.** Inventory local versus WSL extension placement and verify the active remote extension scope.
4. **Step 4.4d: active.** Verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e:** resolve only demonstrated profile-scope conflicts without manually deleting remote extension directories, then run the final Step 4.4 checkpoint.

Later substeps are not authorised merely by being listed. Each begins only after the previous substep's evidence is reviewed.

## Step 4.4a completion result

The corrected read-only recovery verification passed:

```text
stopped_server_recovery_check=PASS
machine_settings_check=PASS
remote_user_settings_check=PASS
extensions_registry_check=PASS
extension_directories_check=PASS
remote_profiles_check=PASS
server_root_directories_check=PASS
projects_root_check=PASS
workspace_candidate_absent_check=PASS
wsl_code_command_invoked=NO_BY_DESIGN
step_4_4a_recovery_verification=PASS
```

Verified baseline:

- user: `akcoo`, UID/GID `1000:1000`;
- home: `/home/akcoo`;
- distribution: Ubuntu `24.04.2 LTS`;
- kernel: `6.6.114.1-microsoft-standard-WSL2`;
- source root: `/home/akcoo/projects`, owner `akcoo:akcoo`, mode `755`, filesystem `ext4`;
- no existing local `career-os` clone;
- VS Code Server stopped before connection;
- WSL machine settings hash: `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- remote user settings file absent;
- WSL extension registry hash before connection: `ae1c24379af094733c0d4360f835827958d1de4135869a9ea1bc83ee2baf15ad`;
- WSL user-extension registry count before connection: `32`;
- WSL user-extension registry Copilot count: `0`;
- `python.defaultInterpreterPath="/bin/python3"` at WSL machine scope;
- no WSL machine-level test, terminal-profile, Copilot, inline-suggestion, or `chat.disableAIFeatures` setting.

Older excluded extension packages remain in shared WSL storage. Their presence on disk does not make them active in the Career OS profile. Do not manually delete them.

## Step 4.4b completion result

The approved harmless workspace was created:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

Creation verification:

```text
workspace_owner=akcoo:akcoo
workspace_mode=755
workspace_filesystem=ext4
workspace_entry_count=0
workspace_owner_check=PASS
workspace_mode_check=PASS
workspace_filesystem_check=PASS
workspace_empty_check=PASS
wsl_code_command_invoked=NO
step_4_4b_workspace_creation=PASS
```

Visual verification established that:

- VS Code was opened from Windows rather than through the WSL `code` command;
- `Career OS Engineering` remained active;
- the window connected to Ubuntu WSL;
- the status indicator showed the Ubuntu WSL context;
- the Explorer showed only the approved empty folder;
- the window was not in a Dev Container;
- no setting, extension, or Settings Sync action occurred;
- the WSL window remained open.

## Step 4.4c completion result

### Installed extension placement

The Extensions view showed:

```text
Local Installed (15)
```

Local entries were exactly the approved Career OS set:

```text
Dev Containers
Jupyter Keymap
WSL
Container Tools
GitHub Pull Requests
Jupyter
Jupyter Cell Tags
Jupyter Notebook Renderers
Jupyter Slide Show
markdownlint
Pylance
Python
Python Debugger
Python Environments
Ruff
```

The Ubuntu WSL section showed:

```text
WSL: Ubuntu - Installed (1)
GitHub Pull Requests
```

The Recommended section listed Azure Tools, Kubernetes, and GitLens. Recommendations are not installed or enabled profile membership and were not acted upon.

### Enabled user-extension scope

The `@enabled` filter showed only four approved user extensions:

```text
Dev Containers
GitHub Pull Requests
Jupyter Keymap
WSL
```

No excluded extension family appeared enabled.

### Copilot installed inventory

The `@installed copilot` filter returned no results.

The earlier WSL user-extension registry inventory also contained no Copilot package. Therefore no user-installed Copilot extension is present locally for this profile or in the WSL user-extension registry.

### Running extension hosts

The Running Extensions editor showed these user or approved extensions:

- `Dev Containers`, no WSL host suffix displayed;
- `WSL`, no WSL host suffix displayed;
- `GitHub Pull Requests (WSL: Ubuntu)`.

It also showed built-in VS Code extensions, including:

- `GitHub Copilot Chat (WSL: Ubuntu)`;
- `GitHub (WSL: Ubuntu)`;
- `Git (WSL: Ubuntu)`;
- `Terminal Suggest for VS Code (WSL: Ubuntu)`;
- `Emmet (WSL: Ubuntu)`;
- `Merge Conflict (WSL: Ubuntu)`;
- `Git Base (WSL: Ubuntu)`;
- `Node Debug Auto-attach (WSL: Ubuntu)`;
- Microsoft Account;
- GitHub Authentication.

No excluded user extension was running.

### Copilot host interpretation

Current VS Code releases ship GitHub Copilot Chat as a built-in extension. The built-in extension may run in the WSL extension host even when `@installed copilot` is empty and the WSL user-extension registry contains no Copilot package.

That host placement is accepted because Career OS deliberately preserves manual chat while disabling automatic AI behavior. The acceptance boundary remains:

- no user-installed Copilot extension in the local or WSL installed inventories;
- no Copilot package in the WSL user-extension registry;
- the five automatic AI safety settings remain enforced;
- `chat.disableAIFeatures` remains unset.

The durable clarification is recorded in `standards/vscode-environment.md`.

### Step 4.4c result

- `Career OS Engineering` remained selected;
- Ubuntu WSL remained active;
- local profile membership remained exactly the approved `15` entries;
- the only WSL-installed user extension shown was GitHub Pull Requests;
- only approved user extensions appeared enabled or running;
- no excluded WSL package became active merely because it exists in shared remote storage;
- no user-installed Copilot extension was present;
- no extension or setting action occurred;
- result: `step_4_4c_extension_scope=PASS`.

## Definition of done for Step 4.4d

Step 4.4d is complete only when the integrated terminal and read-only inspection prove:

- the shell is running inside Ubuntu WSL as `akcoo`, UID/GID `1000:1000`;
- the terminal working directory is `/home/akcoo/projects/career-os-vscode-wsl-check`;
- the workspace is on `ext4`, not `/mnt/c`;
- the shell is Bash and no unexpected terminal-profile override is required;
- `/bin/python3` exists and reports the Ubuntu diagnostic Python version;
- the WSL machine setting remains `python.defaultInterpreterPath="/bin/python3"`;
- no project dependency is installed into Ubuntu system Python;
- no global pytest or unittest selection exists;
- the Career OS profile automatic AI settings remain effective in the WSL window;
- the approved empty workspace remains otherwise unchanged;
- the WSL window remains open for Step 4.4e.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not add extensions merely because they are popular.
- Do not configure a global project interpreter or test framework.
- Ubuntu system Python may be used only for operating-system diagnostics and lightweight host checks; do not install project dependencies into it.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known. Step 4.4d requires the approved integrated-terminal and WSL-setting verification from the open Ubuntu WSL workspace.

## Next action

Open one integrated terminal in the existing WSL window. Run the approved read-only Step 4.4d verification. Return the complete output and leave the WSL window open. Do not change terminal, interpreter, extension, or setting configuration.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
