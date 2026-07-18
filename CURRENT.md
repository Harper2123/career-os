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

Steps 4.4a through 4.4d are complete. Step 4.4e live remote verification is complete. The current subtask is **Step 4.4e closed-window preservation checkpoint**.

No profile-scope conflict has been demonstrated. Therefore no extension, setting, interpreter, terminal, profile, or server correction is authorised.

The next checkpoint must:

1. close VS Code normally;
2. prove that Windows VS Code processes stop;
3. prove that the Ubuntu VS Code Server stops cleanly;
4. prove that the Windows profile, settings, extensions, WSL machine settings, remote registry, remote profile storage, and empty workspace remain preserved.

Do not begin Step 4.5 until Step 4.4e is complete and explicitly recorded.

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
4. **Step 4.4d: complete.** Verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e: active.** Live remote checkpoint complete; closed-window preservation checkpoint pending.

Later top-level Step 4 work is not authorised merely by being listed.

## Step 4.4a result

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

Baseline before the WSL connection:

- user `akcoo`, UID/GID `1000:1000`;
- Ubuntu `24.04.2 LTS` on WSL2;
- source root `/home/akcoo/projects`, owner `akcoo:akcoo`, mode `755`, filesystem `ext4`;
- no existing local `career-os` clone;
- VS Code Server process count `0`;
- WSL machine settings hash `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- remote user settings absent;
- WSL extension registry hash `ae1c24379af094733c0d4360f835827958d1de4135869a9ea1bc83ee2baf15ad`;
- WSL user-extension registry count `32`;
- WSL user-extension registry Copilot count `0`;
- WSL machine setting `python.defaultInterpreterPath="/bin/python3"`;
- no WSL machine-level test, terminal-profile, Copilot, inline-suggestion, or `chat.disableAIFeatures` setting.

Older excluded extension packages remain in shared WSL storage. Their presence on disk does not make them active in the Career OS profile. Do not manually delete them.

## Step 4.4b result

The approved workspace was created and opened:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

Verified:

- owner `akcoo:akcoo`;
- mode `755`;
- filesystem `ext4`;
- empty workspace;
- VS Code opened from Windows, not by WSL `code`;
- `Career OS Engineering` remained active;
- Ubuntu WSL remote context remained active;
- no Dev Container;
- no setting, extension, or Settings Sync action occurred.

Result:

```text
step_4_4b_workspace_creation=PASS
```

## Step 4.4c result

Extension placement and active scope were accepted:

- local profile inventory: exactly the approved `15` entries;
- WSL-installed user extension shown: GitHub Pull Requests only;
- enabled user extensions shown: Dev Containers, GitHub Pull Requests, Jupyter Keymap, and WSL;
- no excluded user extension family was enabled or running;
- `@installed copilot` returned no result;
- the WSL user-extension registry contained no Copilot package;
- built-in GitHub Copilot Chat ran in the WSL extension host, which is accepted because manual chat is preserved while automatic AI behavior remains disabled;
- no extension or setting action occurred.

Result:

```text
step_4_4c_extension_scope=PASS
```

The built-in Copilot host interpretation is recorded in `standards/vscode-environment.md`.

## Step 4.4d result

The integrated-terminal and interpreter-boundary verification passed:

```text
step_4_4d_terminal_interpreter_boundary=PASS
```

Verified terminal and environment state:

- user `akcoo`, UID/GID `1000:1000`;
- working directory `/home/akcoo/projects/career-os-vscode-wsl-check`;
- shell `/usr/bin/bash`;
- `TERM_PROGRAM=vscode`;
- `TERM_PROGRAM_VERSION=1.129.1`;
- WSL distribution `Ubuntu`;
- kernel `6.6.114.1-microsoft-standard-WSL2`;
- workspace owner `akcoo:akcoo`, mode `755`, filesystem `ext4`, mount target `/`;
- workspace remained empty and outside `/mnt`;
- no active virtual environment, Conda environment, or `PYTHONPATH`;
- `/bin/python3` resolved to `/usr/bin/python3.12` and reported Ubuntu diagnostic Python `3.12.3`;
- system Python prefix and base prefix both `/usr`;
- no package installation or interpreter selection occurred;
- machine, Career OS, remote-user-settings, and workspace snapshots remained unchanged.

## Step 4.4e live remote checkpoint result

The live remote checkpoint passed:

```text
step_4_4e_live_remote_checkpoint=PASS
```

### Client and server update classification

A normal VS Code update occurred during Step 4.4:

```text
Previous recorded version: 1.127.0
Current client version: 1.129.1
Current active WSL Server version: 1.129.1
Current active WSL Server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
Version transition: UPDATE_OBSERVED
```

The client and active server versions matched. The active process set and product metadata resolved to the same current server commit. This is classified as an application update, not a Career OS profile failure.

### Preserved settings and workspace

- WSL machine settings hash remained `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- Career OS settings hash remained `fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada`;
- remote user settings remained absent;
- workspace hash remained `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`, confirming the folder remained empty.

### Current WSL remote-storage checkpoint

The WSL connection and normal extension updates produced a new accepted live baseline:

```text
WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
```

The remote user-extension registry remained parseable with `32` entries. Ruff and GitHub Pull Requests were updated to the already approved local versions. The registry contained no Copilot package.

Twenty excluded extension packages remain stored in shared WSL extension storage. Step 4.4c proved that none appeared as active profile membership or a running excluded user extension. They remain classified as stored but inactive. No deletion is authorised.

### Live stability result

All settings, registry, extension-directory, remote-profile, and workspace snapshots remained unchanged during the live read-only check.

No profile correction, extension-state change, setting change, package installation, or manual directory deletion occurred.

## Definition of done for Step 4.4e closed-window checkpoint

Step 4.4e is complete only when read-only evidence after a normal VS Code close proves:

- no Windows VS Code process remains;
- the Ubuntu VS Code Server process count reaches zero without killing processes or deleting server files;
- Windows client version remains `1.129.1`;
- the only non-default profile remains `Career OS Engineering`, directory ID `-639a60a5`;
- Career OS extension membership remains exactly the approved `15` entries;
- Default extension membership remains `36`;
- Default and Career OS settings hashes remain the verified Step 4.3 values;
- Default and Career OS keybindings remain absent;
- WSL machine settings and Career OS settings hashes remain unchanged;
- remote user settings remain absent;
- the accepted current WSL registry, extension-directory, and remote-profile snapshots remain unchanged;
- the registry remains parseable with `32` entries and no Copilot package;
- the approved workspace remains empty;
- no process is killed, no extension state is changed, and no directory is manually deleted.

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

Step 4.4e cannot close until the normal-close Windows and Ubuntu preservation checks pass.

## Next action

Close VS Code normally. Then run the approved Windows PowerShell and Ubuntu read-only closed-window verification blocks from the active setup conversation. Return both complete outputs. Do not reopen VS Code or change any state.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
