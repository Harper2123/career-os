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

Step 4.3 is complete. The current subtask is **Step 4.4a: run a read-only WSL workspace-candidate and remote-state preflight before opening any WSL folder in VS Code**.

During Step 4.4a:

- do not run the WSL `code` command;
- do not open VS Code or connect it to WSL;
- do not create, delete, rename, or edit files or directories;
- do not install, uninstall, enable, disable, or manually delete extensions;
- do not change WSL machine settings, profile settings, Settings Sync, interpreters, terminals, tests, keybindings, or Copilot controls;
- do not begin Step 4.5.

## Step 4.3 completion checkpoint

The final Windows-side checkpoint passed:

```text
step_4_3e_windows_profile_checkpoint=PASS
```

Visual verification established that `Career OS Engineering` launched as the selected folderless profile and that neither WSL nor Dev Container was active.

### Profile identity

- Visible profile name: `Career OS Engineering`.
- Created from `Empty Profile`, not Default or a template.
- Persistent profile directory ID: `-639a60a5`.
- It is the only non-default profile directory.
- The Default profile remains present.
- Settings Sync was not changed.
- No folder or workspace association existed at the Step 4.3 checkpoint.

### Career OS extension baseline

Career OS extension membership is exactly `15`:

```text
charliermarsh.ruff@2026.62.0
davidanson.vscode-markdownlint@0.61.2
github.vscode-pull-request-github@0.158.0
ms-azuretools.vscode-containers@2.4.5
ms-python.debugpy@2026.6.0
ms-python.python@2026.4.0
ms-python.vscode-pylance@2026.2.1
ms-python.vscode-python-envs@1.36.0
ms-toolsai.jupyter@2025.9.1
ms-toolsai.jupyter-keymap@1.1.2
ms-toolsai.jupyter-renderers@1.3.0
ms-toolsai.vscode-jupyter-cell-tags@0.1.9
ms-toolsai.vscode-jupyter-slideshow@0.1.6
ms-vscode-remote.remote-containers@0.466.0
ms-vscode-remote.remote-wsl@0.104.3
```

Default extension membership remains `36`.

### Career OS settings

```json
{
  "files.eol": "\n",
  "git.autofetch": true,
  "git.confirmSync": true,
  "[python]": {
    "editor.defaultFormatter": "charliermarsh.ruff",
    "editor.formatOnSave": true
  },
  "editor.inlineSuggest.enabled": false,
  "github.copilot.enable": {
    "*": false
  },
  "github.copilot.nextEditSuggestions.enabled": false,
  "github.copilot.renameSuggestions.triggerAutomatically": false,
  "github.copilot.editor.enableCodeActions": false
}
```

Verified boundaries:

- no Windows Python interpreter is configured in the Career OS profile;
- no global pytest or unittest selection is configured;
- no terminal default profile is configured;
- no Ruff rule configuration is present;
- no keybindings are present;
- `chat.disableAIFeatures` remains unset;
- manual chat remains available only when deliberately invoked;
- automatic AI completion and editing surfaces are disabled across Default and Career OS profiles.

### Windows settings hashes

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

1. **Step 4.4a: active.** Read-only WSL workspace-candidate and remote-state preflight.
2. **Step 4.4b:** open the approved harmless WSL folder with `Career OS Engineering` and confirm profile and remote-context continuity.
3. **Step 4.4c:** inventory local versus WSL extension placement and verify the active remote extension scope.
4. **Step 4.4d:** verify the integrated Linux terminal, WSL settings, and interpreter boundary.
5. **Step 4.4e:** resolve only demonstrated profile-scope conflicts without manually deleting remote extension directories, then run the final Step 4.4 checkpoint.

Later substeps are not authorised merely by being listed. Each begins only after the previous substep's evidence is reviewed.

## Verified WSL baseline before Step 4.4

- WSL user: `akcoo`, UID/GID `1000:1000`.
- Distribution: Ubuntu 24.04.
- Source root: `/home/akcoo/projects` on the Linux filesystem.
- VS Code Server version: `1.127.0`.
- VS Code Server commit: `4fe60c8b1cdac1c4c174f2fb180d0d758272d713`.
- The WSL server matches the Windows client.
- Remote extension registry count before profile-specific WSL validation: `32`.
- No remote GitHub Copilot extension is registered.
- WSL machine setting `python.defaultInterpreterPath="/bin/python3"` remains diagnostic only.
- The last corrected stopped-server check found zero active VS Code Server processes.

## Definition of done for Step 4.4a

Step 4.4a is complete only when a read-only Ubuntu preflight proves:

- the current user, distribution, kernel, and home directory are expected;
- `/home/akcoo/projects` exists, is owned by `akcoo`, and is on the Linux filesystem;
- immediate candidate folders under `/home/akcoo/projects` are inventoried without exposing private file contents;
- any existing `career-os` clone is identified with its Git branch and clean or dirty state;
- the exact approved temporary workspace path is confirmed absent or its existing state is classified;
- the current VS Code Server process state is measured without grep self-matching;
- the WSL machine settings file and remote extension registry are hashed and inventoried without modification;
- the WSL `code` command is not invoked;
- all read-only stability checks pass.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned installation directories.
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

No technical blocker is known. Step 4.4a requires the approved read-only WSL preflight output.

## Next action

Run the Step 4.4a Ubuntu preflight exactly as provided in the active setup conversation. Return the complete output. Then stop before opening VS Code or creating a workspace.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
