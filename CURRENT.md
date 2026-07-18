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

**Step 4.4 is complete.**

Step 4.5 is not active. It requires the explicit gate:

```text
Proceed to Step 4.5
```

Until that gate is given:

- do not reopen VS Code for Step 4 validation work;
- do not delete the temporary WSL workspace;
- do not change extensions, settings, interpreters, tests, terminals, profiles, Settings Sync, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 5.

## Step 4 implementation status

1. **Step 4.1: complete.** Inventory the existing Windows and WSL VS Code state.
2. **Step 4.2: complete.** Define the minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Create and verify the Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** Validate WSL profile continuity, extension scope, terminal context, settings, interpreter boundaries, and closed-window preservation.
5. **Step 4.5: awaiting explicit approval.** Validate editor workflows for Python, Ruff, Markdown, tests, Git, GitHub pull requests, and the integrated terminal.
6. **Step 4.6:** validate Container Tools and repository-owned Dev Containers.
7. **Step 4.7:** verify the automatic AI boundary end to end.
8. **Step 4.8:** run the final harmless end-to-end workflow and remove only explicitly disposable artifacts.

Later steps are not authorised merely by being listed.

## Step 4.3 Windows profile checkpoint

The final Windows profile checkpoint passed:

```text
step_4_3e_windows_profile_checkpoint=PASS
```

Verified profile state:

- profile name: `Career OS Engineering`;
- created from Empty Profile;
- persistent profile directory ID: `-639a60a5`;
- only non-default profile directory;
- Career OS extension membership: exactly `15` approved entries;
- Default extension membership: `36`;
- no Windows Python interpreter configured in the Career OS profile;
- no global test framework, terminal profile, Ruff rule configuration, or keybindings;
- automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions disabled across Default and Career OS profiles;
- `chat.disableAIFeatures` unset so deliberate manual chat remains available;
- Settings Sync unchanged.

Verified Windows settings hashes:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

## Step 4.4 completion result

All Step 4.4 substeps passed.

### Step 4.4a: read-only WSL preflight

The corrected recovery verification passed:

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

Verified pre-connection baseline:

- user `akcoo`, UID/GID `1000:1000`;
- Ubuntu `24.04.2 LTS` on WSL2;
- source root `/home/akcoo/projects`, owner `akcoo:akcoo`, mode `755`, filesystem `ext4`;
- no existing local `career-os` clone;
- VS Code Server stopped before connection;
- WSL machine setting `python.defaultInterpreterPath="/bin/python3"`;
- no WSL machine-level test, terminal-profile, Copilot, inline-suggestion, or `chat.disableAIFeatures` setting;
- WSL user-extension registry count `32`, with no Copilot package.

### Step 4.4b: WSL workspace and profile continuity

The approved temporary workspace is:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

Verified:

- owner `akcoo:akcoo`;
- mode `755`;
- filesystem `ext4`;
- workspace empty;
- VS Code opened from Windows, not by the WSL `code` command;
- `Career OS Engineering` remained selected after the WSL transition;
- Ubuntu WSL context remained active;
- no Dev Container;
- no setting, extension, profile, or Settings Sync action occurred.

Result:

```text
step_4_4b_workspace_creation=PASS
```

### Step 4.4c: extension placement and active scope

Verified:

- local profile inventory remained exactly the approved `15` extensions;
- the WSL-installed user extension shown was GitHub Pull Requests;
- enabled user extensions shown were Dev Containers, GitHub Pull Requests, Jupyter Keymap, and WSL;
- no excluded user-extension family was enabled or running;
- `@installed copilot` returned no result;
- the WSL user-extension registry contained no Copilot package;
- built-in GitHub Copilot Chat ran in the WSL extension host, which is accepted because manual chat is preserved while automatic AI behaviour remains disabled;
- no extension or setting action occurred.

Result:

```text
step_4_4c_extension_scope=PASS
```

The built-in Copilot host interpretation is recorded in `standards/vscode-environment.md`.

Twenty excluded extension packages remain stored in shared WSL extension storage. They are classified as stored but inactive. No deletion is authorised.

### Step 4.4d: terminal and interpreter boundary

Verified:

- integrated terminal user `akcoo`, UID/GID `1000:1000`;
- working directory `/home/akcoo/projects/career-os-vscode-wsl-check`;
- shell `/usr/bin/bash`;
- `TERM_PROGRAM=vscode`;
- Ubuntu WSL distribution and WSL2 kernel;
- workspace on `ext4`, outside `/mnt`;
- no active virtual environment, Conda environment, or `PYTHONPATH`;
- no `.venv`, `venv`, or `.conda` path in the workspace;
- `/bin/python3` resolved to `/usr/bin/python3.12` and reported Ubuntu diagnostic Python `3.12.3`;
- system Python prefix and base prefix both `/usr`;
- no package installation or interpreter selection occurred;
- machine settings, Career OS settings, remote-user-settings state, and workspace remained unchanged.

Result:

```text
step_4_4d_terminal_interpreter_boundary=PASS
```

### Step 4.4e: live and closed-window preservation

The live checkpoint passed:

```text
step_4_4e_live_remote_checkpoint=PASS
```

A normal VS Code update was observed and classified:

```text
Previous recorded version: 1.127.0
Current client version: 1.129.1
Current WSL Server version: 1.129.1
Current client and server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
Version transition: UPDATE_OBSERVED
```

The client and active WSL Server matched. This was an application update, not a profile failure.

Accepted current WSL remote-storage baselines:

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
Workspace hash: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
```

The Windows closed-window checkpoint passed:

```text
windows_code_process_check=PASS
client_version_check=PASS
client_commit_check=PASS
profile_identity_check=PASS
default_settings_hash_check=PASS
career_settings_hash_check=PASS
keybindings_absent_check=PASS
career_extension_membership_check=PASS
default_extension_count_check=PASS
career_user_installed_copilot_check=PASS
windows_settings_stability_check=PASS
windows_keybindings_stability_check=PASS
career_extensions_stability_check=PASS
default_extensions_stability_check=PASS
step_4_4e_windows_closed_checkpoint=PASS
```

The Ubuntu closed-window checkpoint passed:

```text
vscode_server_stopped_check=PASS
stored_server_version_check=PASS
stored_server_commit_check=PASS
machine_settings_hash_check=PASS
career_settings_hash_check=PASS
remote_user_settings_hash_check=PASS
extensions_registry_hash_check=PASS
extension_directories_hash_check=PASS
remote_profiles_hash_check=PASS
workspace_hash_check=PASS
closed_registry_count_check=PASS
closed_registry_copilot_check=PASS
closed_registry_parse=PASS
workspace_stability_check=PASS
step_4_4e_ubuntu_closed_checkpoint=PASS
```

Final preservation evidence:

- Windows VS Code process count reached zero after a normal close;
- Ubuntu VS Code Server process count was zero on the first check;
- no process was killed;
- no WSL shutdown was performed;
- no extension state changed;
- no setting changed;
- no directory was manually deleted;
- VS Code remained closed throughout both final checks;
- no warning or error appeared;
- the temporary workspace remains empty and preserved for later Step 4 validation or cleanup.

Overall Step 4.4 result:

```text
step_4_4_wsl_profile_validation=PASS
```

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not add extensions merely because they are popular.
- Do not configure a global project interpreter or test framework.
- Ubuntu system Python may be used only for operating-system diagnostics and lightweight host checks. Do not install project dependencies into it.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known.

Step 4.5 is blocked only by the workflow gate. It must not begin until Ayush explicitly says:

```text
Proceed to Step 4.5
```

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
