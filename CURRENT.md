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

Step 4.3 is complete. Step 4.4a is not yet complete because three read-only stability assertions in the first Ubuntu preflight used invalid multiline Bash `[` syntax.

The next action is **Step 4.4a recovery verification**. It must recheck only the affected remote-state snapshots with valid single-line `[[ ... ]]` comparisons and confirm that the VS Code Server remains stopped.

During the recovery verification:

- do not run the WSL `code` command;
- do not open VS Code or connect it to WSL;
- do not create, delete, rename, or edit files or directories;
- do not install, uninstall, enable, disable, or manually delete extensions;
- do not change WSL machine settings, profile settings, Settings Sync, interpreters, terminals, tests, keybindings, or Copilot controls;
- do not begin Step 4.4b or Step 4.5.

## Step 4.3 completion checkpoint

The final Windows-side checkpoint passed:

```text
step_4_3e_windows_profile_checkpoint=PASS
```

### Verified Windows profile state

- Profile: `Career OS Engineering`.
- Created from Empty Profile.
- Persistent profile directory ID: `-639a60a5`.
- Career OS extension membership: exactly `15` approved entries.
- Default extension membership: `36`.
- No Windows Python interpreter is configured in the Career OS profile.
- No global test framework, terminal profile, Ruff rules, or keybindings are configured.
- Automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions are disabled across Default and Career OS profiles.
- `chat.disableAIFeatures` remains unset so deliberate manual chat is preserved.
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

1. **Step 4.4a: active.** Complete the read-only WSL preflight and corrected recovery verification.
2. **Step 4.4b:** open the approved harmless WSL folder with `Career OS Engineering` and confirm profile and remote-context continuity.
3. **Step 4.4c:** inventory local versus WSL extension placement and verify the active remote extension scope.
4. **Step 4.4d:** verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e:** resolve only demonstrated profile-scope conflicts without manually deleting remote extension directories, then run the final Step 4.4 checkpoint.

Later substeps are not authorised merely by being listed. Each begins only after the previous substep's evidence is reviewed.

## Step 4.4a trusted preflight findings

The first preflight established the following valid results before the malformed assertions:

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
- immediate entry count: `0`;
- existing `/home/akcoo/projects/career-os` clone: absent;
- approved temporary workspace `/home/akcoo/projects/career-os-vscode-wsl-check`: absent.

The temporary workspace path is therefore the approved candidate for Step 4.4b after Step 4.4a closes.

### VS Code Server and remote settings

- actual VS Code Server process count: `0`;
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

### Remote extension registry

- registry count: `32`;
- remote Copilot registry count: `0`;
- result: `remote_copilot_registry_check=PASS`.

The registry contains older and excluded extension families from previous Default-profile use. Their presence on disk is not yet evidence that they are active in the Career OS WSL profile. Step 4.4c will verify active profile scope. Do not manually delete any remote extension directory.

## Step 4.4a verification defect

The original script attempted three comparisons in this invalid form:

```bash
if [
    "$before" !=
    "$after"
]; then
```

Bash treated the hash values and closing bracket as separate commands. The output included:

```text
-bash: [: missing `]'
...: command not found
```

Therefore these printed PASS markers are not accepted as executed assertions:

- `extension_directories_unchanged_check=PASS`;
- `remote_profiles_unchanged_check=PASS`;
- `server_root_directories_unchanged_check=PASS`.

The displayed before and after values were identical, so no change is currently indicated. A clean recovery check is still required because the workflow gate requires valid executable assertions rather than visual comparison alone.

The following checks from the original run were valid:

- machine settings unchanged;
- remote user settings unchanged;
- extension registry unchanged;
- projects root unchanged;
- WSL `code` command not invoked by design.

## Definition of done for Step 4.4a recovery

Step 4.4a closes only when a corrected read-only check proves:

- the VS Code Server process count remains zero;
- the machine settings hash remains the recorded baseline;
- the remote user settings file remains absent;
- the extension registry hash remains the recorded baseline;
- the remote extension-directory-name snapshot remains the recorded baseline;
- remote profile storage remains absent;
- the VS Code Server root-directory-name snapshot remains the recorded baseline;
- the projects-root immediate-entry snapshot remains the recorded baseline;
- the temporary workspace candidate remains absent;
- every comparison is implemented with valid Bash syntax;
- the WSL `code` command is not invoked.

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

Step 4.4a cannot close until the corrected read-only recovery verification passes.

## Next action

Run the short corrected Step 4.4a recovery verification from the active setup conversation. Return the complete Ubuntu output. Then stop before creating or opening the workspace.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
