# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` represents the last merged top-level checkpoint.
- All Step 4 substeps are completed on this branch.
- One pull request will be created only after the full Step 4 completion condition is verified.
- Unrelated work must not be added to this branch.

This branch model is governed by `decisions/0002-use-one-branch-per-setup-step.md`.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The setup must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.3 is active.**

Steps 4.3a through 4.3d are complete. The current subtask is **Step 4.3e: run the final Windows-side profile verification and record the Step 4.3 checkpoint**.

During Step 4.3e, do not change settings, extensions, Settings Sync, profile associations, interpreters, tests, terminals, keybindings, Copilot controls, or begin Step 4.4.

## Verified Step 4.3 profile state

### Profile

- Visible profile name: `Career OS Engineering`.
- Created from `Empty Profile`, not Default or a template.
- Persistent profile directory ID: `-639a60a5`.
- Default profile remains present.
- Settings Sync was not changed.
- No folder or workspace association has been created.

### Career OS extension baseline

Final verified profile extension count: `15`.

Approved direct extensions:

```text
ms-vscode-remote.remote-wsl@0.104.3
ms-vscode-remote.remote-containers@0.466.0
ms-azuretools.vscode-containers@2.4.5
github.vscode-pull-request-github@0.158.0
ms-python.python@2026.4.0
charliermarsh.ruff@2026.62.0
ms-toolsai.jupyter@2025.9.1
davidanson.vscode-markdownlint@0.61.2
```

Accepted supporting extensions:

```text
ms-python.debugpy@2026.6.0
ms-python.vscode-pylance@2026.2.1
ms-python.vscode-python-envs@1.36.0
ms-toolsai.jupyter-keymap@1.1.2
ms-toolsai.jupyter-renderers@1.3.0
ms-toolsai.vscode-jupyter-cell-tags@0.1.9
ms-toolsai.vscode-jupyter-slideshow@0.1.6
```

Verification:

- all eight direct extensions are present;
- all seven additional extensions are approved dependencies or companions;
- unexpected extension count is `0`;
- excluded extension count is `0`;
- result: `step_4_3b_extension_baseline=PASS`.

### Career OS non-AI settings

```json
{
  "files.eol": "\n",
  "git.autofetch": true,
  "git.confirmSync": true,
  "[python]": {
    "editor.defaultFormatter": "charliermarsh.ruff",
    "editor.formatOnSave": true
  }
}
```

Verification:

- no Windows Python interpreter is configured;
- no global pytest or unittest selection is configured;
- no terminal default profile is configured;
- no Ruff rule configuration is present;
- no keybindings are present;
- Step 4.3c settings SHA-256 baseline was `91ED7B862D2342F415C5C99F5E1EACCC4E8FFD1145546DE922B36E4E68A6A0A4`;
- result: `step_4_3c_minimum_settings=PASS`.

### Automatic AI boundary

The five approved safety settings were set from a folderless `Career OS Engineering` window and marked **Apply Setting to all Profiles**:

```json
{
  "editor.inlineSuggest.enabled": false,
  "github.copilot.enable": {
    "*": false
  },
  "github.copilot.nextEditSuggestions.enabled": false,
  "github.copilot.renameSuggestions.triggerAutomatically": false,
  "github.copilot.editor.enableCodeActions": false
}
```

File-level verification established:

- Default and Career OS each contain the exact wildcard-only `github.copilot.enable` map;
- generic inline suggestions are disabled;
- next-edit suggestions are disabled;
- automatic rename suggestions are disabled;
- automatic AI code actions are disabled;
- `chat.disableAIFeatures` remains unset in both profiles;
- manual chat is not globally removed;
- the Career OS non-AI settings and Python block remain unchanged;
- no prohibited interpreter, test, terminal, or Ruff setting appeared;
- Career OS extension membership remains `15`;
- Default extension membership remains `36`;
- Default and Career OS keybindings remain absent;
- settings and extension state did not change during the read-only verification;
- result: `step_4_3d_ai_boundary=PASS`.

Current settings hashes after Step 4.3d:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

Known Default-profile legacy settings were preserved:

- `editor.formatOnSave=true`;
- `git.autofetch=true`;
- `git.confirmSync=false`;
- `python.defaultInterpreterPath="c:\\msys64\\ucrt64\\bin\\python.exe"`.

## Definition of done for Step 4.3e

Step 4.3e is complete only when a final Windows-side verification proves:

- the only non-default profile is `Career OS Engineering` with directory ID `-639a60a5`;
- the profile launches folderless and is visibly selected;
- its extension membership is exactly the approved `15` entries;
- Default extension membership remains `36`;
- both current settings hashes match the Step 4.3d baselines;
- both Copilot maps remain exactly `{ "*": false }`;
- the other four automatic-AI safety settings remain false in both profiles;
- `chat.disableAIFeatures` remains unset;
- the Career OS non-AI settings remain correct;
- no keybinding or workspace association exists;
- no state changes during the final verification.

## Step 4.3 staged implementation

1. **Step 4.3a: complete.** Create and verify the empty profile.
2. **Step 4.3b: complete.** Install and verify the approved extension baseline.
3. **Step 4.3c: complete.** Apply and verify the minimum non-AI profile settings.
4. **Step 4.3d: complete.** Apply and verify the automatic AI boundary across both profiles.
5. **Step 4.3e: active.** Run the final Windows-side profile verification and record the checkpoint.

Step 4.4 is not authorised merely by being listed after Step 4.3.

## Approved Step 4.2 architecture

The governing standard is `standards/vscode-environment.md`.

### Runtime boundary

- Do not configure a Windows Python interpreter in the Career OS profile.
- Ubuntu system Python remains diagnostic and receives no project dependencies.
- Substantial Python projects use repository-owned Dev Containers.
- Each repository owns its test configuration.

### AI boundary

Automatic AI completion remains disabled across profiles. Manual chat may remain available only when deliberately invoked after a first attempt. Do not set `chat.disableAIFeatures=true` in Career OS v1.

## Verified Windows and WSL baseline

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Built-in package `GitHub.copilot-chat` version `0.57.0` is present.

### WSL client state

- WSL user: `akcoo`, UID/GID `1000:1000`.
- Distribution: Ubuntu.
- VS Code Server version: `1.127.0`.
- VS Code Server commit: `4fe60c8b1cdac1c4c174f2fb180d0d758272d713`.
- The WSL server matches the Windows client.
- Remote extension registry count before profile-specific WSL validation: `32`.
- No remote GitHub Copilot extension is registered.
- WSL machine setting `python.defaultInterpreterPath="/bin/python3"` remains diagnostic only.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned installation directories.
- Do not add extensions merely because they are popular.
- Do not configure a global project interpreter or test framework.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known. Step 4.3e requires the final read-only Windows profile verification and a brief visual confirmation that `Career OS Engineering` launches as the selected folderless profile.

## Next action

Run the approved Step 4.3e final Windows verification. Return the complete PowerShell output and the requested visual confirmation. Then stop before Step 4.4.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
