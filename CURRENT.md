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

Steps 4.4a through 4.4d are complete. The current subtask is **Step 4.4e: run the final WSL profile checkpoint and resolve only demonstrated profile-scope conflicts**.

No profile-scope conflict has been demonstrated so far. Therefore no extension, setting, interpreter, terminal, or profile correction is currently authorised.

Step 4.4e will proceed in two reviewed phases:

1. **Live remote checkpoint:** inspect the still-open Ubuntu WSL window and capture current server, profile, workspace, settings, and extension-registry state without modification.
2. **Closed-window preservation checkpoint:** after the live evidence is reviewed, close VS Code normally and verify that Windows and WSL state remain preserved and the server stops cleanly.

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
5. **Step 4.4e: active.** Run the final live and closed-window WSL profile checkpoints. Resolve only demonstrated conflicts.

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

Verified terminal context:

- user `akcoo`, UID/GID `1000:1000`;
- working directory `/home/akcoo/projects/career-os-vscode-wsl-check`;
- shell `/usr/bin/bash`;
- `TERM_PROGRAM=vscode`;
- `TERM_PROGRAM_VERSION=1.129.1`;
- WSL distribution `Ubuntu`;
- kernel `6.6.114.1-microsoft-standard-WSL2`;
- workspace owner `akcoo:akcoo`, mode `755`, filesystem `ext4`, mount target `/`;
- workspace remained empty and outside `/mnt`.

Verified environment boundary:

- no active virtual environment;
- no active Conda environment;
- `PYTHONPATH` unset;
- no `.venv`, `venv`, or `.conda` path in the workspace;
- `/bin/python3` resolved to `/usr/bin/python3.12`;
- Ubuntu diagnostic Python version `3.12.3`;
- system Python prefix and base prefix both `/usr`;
- no package installation was performed;
- no interpreter selection was changed.

Verified settings boundary:

- WSL machine settings hash remained `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- Career OS settings hash remained `fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada`;
- remote user settings remained absent;
- WSL machine setting remained `python.defaultInterpreterPath="/bin/python3"`;
- no machine-level test, terminal-profile, Copilot, inline-suggestion, or `chat.disableAIFeatures` setting appeared;
- Career OS formatting, Git, Python-block, and five automatic-AI safety settings remained exact;
- no prohibited Career OS interpreter, test, terminal, Ruff, or `chat.disableAIFeatures` setting appeared;
- settings and workspace snapshots remained unchanged during the check.

Visual confirmation established that the Ubuntu WSL indicator and `Career OS Engineering` profile remained active and the WSL window remained open.

## Definition of done for Step 4.4e live checkpoint

The live checkpoint is complete only when read-only evidence proves:

- the terminal remains in the approved empty workspace;
- the current VS Code client and active WSL server versions or commits are identified;
- any automatic client or server update since the Step 4.4a baseline is classified rather than treated as a profile failure;
- the current WSL machine settings and Career OS settings hashes remain unchanged;
- remote user settings remain absent;
- the current WSL user-extension registry is parseable and contains no Copilot package;
- excluded remote packages remain merely stored and are not shown as active profile membership;
- the workspace remains empty;
- no correction, installation, deletion, enablement, disablement, or setting change occurs;
- the WSL window remains open until the live evidence is reviewed.

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

No technical blocker is known. Step 4.4e requires the approved live remote checkpoint from the still-open Ubuntu WSL window.

## Next action

Run the approved Step 4.4e live remote checkpoint in the existing integrated terminal. Return the complete output and leave the WSL window open. Do not change extensions, settings, interpreters, terminals, or profiles.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
