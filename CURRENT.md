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

Step 4.4a is complete. The current subtask is **Step 4.4b: create the approved harmless workspace, open it through the Windows VS Code WSL workflow using `Career OS Engineering`, and confirm profile and remote-context continuity**.

During Step 4.4b:

- create only `/home/akcoo/projects/career-os-vscode-wsl-check`;
- do not create files inside it;
- do not run the WSL `code` command;
- do not install, uninstall, enable, disable, or manually delete extensions;
- do not change WSL machine settings, profile settings, Settings Sync, interpreters, terminals, tests, keybindings, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 4.4c, Step 4.5, or Step 5.

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
2. **Step 4.4b: active.** Create the approved harmless folder, open it through the Windows WSL workflow with `Career OS Engineering`, and confirm profile and remote-context continuity.
3. **Step 4.4c:** inventory local versus WSL extension placement and verify the active remote extension scope.
4. **Step 4.4d:** verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e:** resolve only demonstrated profile-scope conflicts without manually deleting remote extension directories, then run the final Step 4.4 checkpoint.

Later substeps are not authorised merely by being listed. Each begins only after the previous substep's evidence is reviewed.

## Step 4.4a completion result

The initial read-only preflight established the expected identity, projects-root, machine-settings, extension-registry, and stopped-server state. Three stability assertions in that first script used invalid multiline Bash `[` syntax, so their printed PASS markers were rejected.

A corrected recovery verification then reran every affected comparison with valid `[[ ... ]]` syntax and passed:

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

### Identity and platform

- user: `akcoo`;
- UID/GID: `1000:1000`;
- home: `/home/akcoo`;
- kernel: `6.6.114.1-microsoft-standard-WSL2`;
- architecture: `x86_64`;
- distribution: Ubuntu `24.04.2 LTS`.

### Projects root and workspace candidate

- `/home/akcoo/projects` exists;
- owner: `akcoo:akcoo`;
- mode: `755`;
- filesystem: `ext4` mounted at `/` from `/dev/sdd`;
- immediate entry count before Step 4.4b: `0`;
- existing `/home/akcoo/projects/career-os` clone: absent;
- approved temporary workspace `/home/akcoo/projects/career-os-vscode-wsl-check`: absent before Step 4.4b.

The approved Step 4.4b workspace is therefore:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

### VS Code Server and remote settings baseline

- VS Code Server process count: `0`;
- process state: stopped;
- WSL machine settings SHA-256: `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- remote user settings file: absent;
- remote extension registry SHA-256: `ae1c24379af094733c0d4360f835827958d1de4135869a9ea1bc83ee2baf15ad`;
- remote extension-directory-name snapshot: `da2cc8ea8a412dcf2d121d1a37ad0844f0d3f0d00db339bf6d869ad3d3ee6db0`;
- remote profile storage: absent;
- VS Code Server root-directory-name snapshot: `f06fdddaeace4b6e43beac91c9017714080bd1da511a71f1db47345813c4c9e6`;
- projects-root immediate-entry snapshot: `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`.

### WSL machine setting boundary

- `python.defaultInterpreterPath="/bin/python3"`;
- no global pytest or unittest setting;
- no Linux terminal default override;
- no WSL machine-level inline-suggestion or Copilot setting;
- `chat.disableAIFeatures` is not set;
- result: `machine_interpreter_boundary=PASS`.

### Remote extension registry baseline

- registry count: `32`;
- remote Copilot registry count: `0`;
- result: `remote_copilot_registry_check=PASS`.

The registry contains older and excluded extension families from previous Default-profile use. Their presence on disk is not evidence that they are active in the Career OS WSL profile. Step 4.4c will verify active profile scope. Do not manually delete any remote extension directory.

## Definition of done for Step 4.4b

Step 4.4b is complete only when:

- `/home/akcoo/projects/career-os-vscode-wsl-check` is created as an empty directory;
- it is owned by `akcoo:akcoo`, mode `755`, and stored on the Linux filesystem;
- VS Code is opened from Windows, not by invoking WSL `code`;
- a new window is opened with the `Career OS Engineering` profile;
- that window connects to the Ubuntu WSL distribution;
- the approved folder is opened in the WSL window;
- `Career OS Engineering` remains visibly active after the remote transition;
- the status indicator shows `WSL: Ubuntu` or the equivalent current Ubuntu WSL label;
- the window is not in a Dev Container;
- the Explorer shows only the approved empty folder;
- no manual extension or setting action occurs;
- the WSL window is left open for Step 4.4c.

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

No technical blocker is known. Step 4.4b requires creating the approved empty folder and opening it through the Windows VS Code WSL workflow while preserving the selected profile.

## Next action

Create the approved empty folder from Ubuntu. Then open a Windows VS Code window with `Career OS Engineering`, connect it to Ubuntu using the WSL command from the Command Palette, open the approved folder, confirm the requested visual state, and leave the WSL window open. Do not change settings or extensions.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
