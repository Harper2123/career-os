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

Steps 4.4a and 4.4b are complete. The current subtask is **Step 4.4c: inventory local versus Ubuntu WSL extension placement and verify the active remote extension scope for the `Career OS Engineering` profile**.

During Step 4.4c:

- keep the approved WSL window open with `Career OS Engineering` active;
- inspect extension placement and active extension hosts without installing, uninstalling, enabling, disabling, or manually deleting anything;
- do not change settings, Settings Sync, profile associations, interpreters, terminals, tests, keybindings, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 4.4d, Step 4.5, or Step 5.

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
3. **Step 4.4c: active.** Inventory local versus WSL extension placement and verify the active remote extension scope.
4. **Step 4.4d:** verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e:** resolve only demonstrated profile-scope conflicts without manually deleting remote extension directories, then run the final Step 4.4 checkpoint.

Later substeps are not authorised merely by being listed. Each begins only after the previous substep's evidence is reviewed.

## Step 4.4a completion result

The initial read-only preflight established the expected identity, projects-root, machine-settings, extension-registry, and stopped-server state. Three stability assertions in that first script used invalid multiline Bash `[` syntax, so their printed PASS markers were rejected.

A corrected recovery verification reran every affected comparison with valid `[[ ... ]]` syntax and passed:

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

### WSL baseline before connection

- user: `akcoo`;
- UID/GID: `1000:1000`;
- home: `/home/akcoo`;
- kernel: `6.6.114.1-microsoft-standard-WSL2`;
- architecture: `x86_64`;
- distribution: Ubuntu `24.04.2 LTS`;
- `/home/akcoo/projects` owner: `akcoo:akcoo`;
- mode: `755`;
- filesystem: `ext4` mounted at `/` from `/dev/sdd`;
- existing `/home/akcoo/projects/career-os` clone: absent;
- VS Code Server process count before connection: `0`;
- WSL machine settings SHA-256: `6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52`;
- remote user settings file: absent;
- remote extension registry SHA-256: `ae1c24379af094733c0d4360f835827958d1de4135869a9ea1bc83ee2baf15ad`;
- remote extension-directory-name snapshot: `da2cc8ea8a412dcf2d121d1a37ad0844f0d3f0d00db339bf6d869ad3d3ee6db0`;
- remote profile storage: absent;
- VS Code Server root-directory-name snapshot: `f06fdddaeace4b6e43beac91c9017714080bd1da511a71f1db47345813c4c9e6`;
- initial projects-root immediate-entry snapshot: `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`.

### WSL machine setting boundary

- `python.defaultInterpreterPath="/bin/python3"`;
- no global pytest or unittest setting;
- no Linux terminal default override;
- no WSL machine-level inline-suggestion or Copilot setting;
- `chat.disableAIFeatures` is not set;
- result: `machine_interpreter_boundary=PASS`.

### Remote extension registry baseline

- registry count before the Career OS WSL connection: `32`;
- remote Copilot registry count: `0`;
- result: `remote_copilot_registry_check=PASS`.

The registry contains older and excluded extension families from previous Default-profile use. Their presence on disk is not evidence that they are active in the Career OS WSL profile. Step 4.4c must verify active profile scope. Do not manually delete any remote extension directory.

## Step 4.4b completion result

The approved harmless workspace was created:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

Creation verification passed:

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
- `Career OS Engineering` remained the active profile;
- the window connected to the Ubuntu WSL distribution;
- the status indicator showed the Ubuntu WSL context;
- the opened folder was `career-os-vscode-wsl-check`;
- the Explorer showed the approved empty folder;
- the window was not in a Dev Container;
- Settings Sync was not changed;
- no setting or extension action occurred;
- the WSL window was left open for Step 4.4c.

## Definition of done for Step 4.4c

Step 4.4c is complete only when read-only evidence proves:

- which approved extensions are installed locally and which are installed in Ubuntu WSL;
- which extension host each currently activated extension uses;
- the `Career OS Engineering` profile remains selected;
- the active WSL profile does not enable excluded extension families merely because older packages exist in the shared remote extension registry;
- no remote Copilot extension is installed or active;
- no extension is installed, uninstalled, enabled, disabled, or manually deleted during inspection;
- the Step 4.3 Windows profile settings and extension baselines remain preserved.

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

No technical blocker is known. Step 4.4c requires a read-only extension placement and active-host inventory from the open Ubuntu WSL window.

## Next action

Use the open `Career OS Engineering` WSL window to inspect the installed-extension categories and the running-extension host locations. Return the requested counts and names without changing any extension or setting. Then stop before opening the integrated terminal for Step 4.4d.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
