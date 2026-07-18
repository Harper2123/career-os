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

Steps 4.3a and 4.3b are complete. The current subtask is **Step 4.3c: apply and verify the minimum non-AI profile settings in `Career OS Engineering`**.

During Step 4.3c, do not change automatic AI settings, Settings Sync, workspace associations, Default-profile settings, terminal profiles, interpreter paths, test-framework settings, Ruff rules, keybindings, extension membership, or begin Step 4.4.

## Step 4.3a result

The approved empty profile was created and verified:

- visible profile name: `Career OS Engineering`;
- created from `Empty Profile`, not Default or a template;
- `Career OS Engineering` was selected for the verification window;
- `Default` remained visible;
- Settings Sync was not changed;
- persistent profile directory ID: `-639a60a5`;
- Career OS profile user-extension count was `0` before Step 4.3b;
- Default profile user-extension count remained `36`;
- Default profile `settings.json` SHA-256 remained `C285A4C03C5727E6A0B1D1B8C65C3371E74F467FD027C559A9CBFFF6A4F7FE28`;
- Default profile `keybindings.json` remained absent;
- result: `step_4_3a_empty_profile=PASS`.

## Step 4.3b result

The first installation wrapper was interrupted by a Node.js `DEP0169` warning on the native error stream. A read-only recovery inventory proved that `ms-vscode-remote.remote-wsl` had been added and that all other state remained safe. Installation then resumed for only the seven missing extensions with native warning output tolerated and real process exit codes checked.

Final verified profile extension count: `15`.

### Approved direct extensions

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

### Accepted supporting extensions

```text
ms-python.debugpy@2026.6.0
ms-python.vscode-pylance@2026.2.1
ms-python.vscode-python-envs@1.36.0
ms-toolsai.jupyter-keymap@1.1.2
ms-toolsai.jupyter-renderers@1.3.0
ms-toolsai.vscode-jupyter-cell-tags@0.1.9
ms-toolsai.vscode-jupyter-slideshow@0.1.6
```

Verification results:

- all eight direct extensions are present;
- all seven additional extensions are approved dependencies or companions;
- unexpected extension count: `0`;
- excluded extension count: `0`;
- Default profile extension membership remained unchanged at `36`;
- Default settings hash remained `C285A4C03C5727E6A0B1D1B8C65C3371E74F467FD027C559A9CBFFF6A4F7FE28`;
- Default keybindings remained absent;
- Career OS profile settings remained absent during extension installation;
- Career OS keybindings remained absent;
- profile directory count and identity remained unchanged;
- result: `step_4_3b_extension_baseline=PASS`.

## Definition of done for Step 4.3c

Step 4.3c is complete only when the Career OS profile contains exactly these non-AI settings:

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

The substep must also prove that:

- no Windows Python interpreter is configured in the profile;
- no global pytest or unittest selection is configured;
- no terminal default profile is configured;
- no Ruff rule configuration is added;
- no AI or Copilot setting is changed yet;
- extension membership remains exactly the approved 15 entries;
- Default profile settings and extension membership remain unchanged;
- no keybindings or workspace association is created.

## Approved Step 4.2 architecture

The governing standard is `standards/vscode-environment.md`.

### Profile

Use one dedicated Empty Profile named:

```text
Career OS Engineering
```

Preserve the Default profile. Do not copy it. Do not change Settings Sync in Career OS v1.

### Runtime boundary

- Do not configure a Windows Python interpreter in the Career OS profile.
- Ubuntu system Python remains diagnostic and receives no project dependencies.
- Substantial Python projects use repository-owned Dev Containers.
- Each repository owns its test configuration.

### Minimum non-AI settings

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

Do not define a global Python interpreter path, test framework, terminal profile, or Ruff rule configuration.

### Automatic AI target for later Step 4.3d

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

Manual chat may remain available only when deliberately invoked after a first attempt. Do not set `chat.disableAIFeatures=true` in Career OS v1.

## Verified Step 4.1 baseline

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Default-profile extension count before Step 4.3: `36`.
- Default-profile `settings.json` baseline SHA-256: `C285A4C03C5727E6A0B1D1B8C65C3371E74F467FD027C559A9CBFFF6A4F7FE28`.
- Default-profile `keybindings.json` was absent.

### Current AI boundary defect

- Built-in package `GitHub.copilot-chat` version `0.57.0` is present.
- `github.copilot.enable` currently enables Python and plaintext in the Default profile.
- `github.copilot.nextEditSuggestions.enabled=true` in the Default profile.
- The required automatic AI completion boundary is not yet satisfied.

### WSL client state

- WSL user: `akcoo`, UID/GID `1000:1000`.
- Distribution: Ubuntu.
- VS Code Server version: `1.127.0`.
- VS Code Server commit: `4fe60c8b1cdac1c4c174f2fb180d0d758272d713`.
- The WSL server matches the Windows client.
- The corrected stopped-server check found zero active VS Code Server processes.
- Remote extension registry count: `32`.
- No remote GitHub Copilot extension is registered.
- WSL machine setting `python.defaultInterpreterPath="/bin/python3"` remains diagnostic only.

## Step 4.3 staged implementation

1. **Step 4.3a: complete.** Create and verify the empty profile.
2. **Step 4.3b: complete.** Install and verify the approved direct extension baseline and accepted supporting extensions.
3. **Step 4.3c: active.** Apply and verify the minimum non-AI profile settings.
4. **Step 4.3d:** apply and verify the automatic AI boundary across the appropriate profile scopes.
5. **Step 4.3e:** complete a final Windows-side profile verification and record the checkpoint.

Step 4.4 is not authorised merely by being listed after Step 4.3.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned installation directories.
- Do not add extensions merely because they are popular.
- Do not configure a global project interpreter or test framework.
- Keep automatic AI completion disabled by default.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known. Step 4.3c requires creating and verifying the exact minimum non-AI settings file for `Career OS Engineering` while preserving all other state.

## Next action

Apply the approved minimum non-AI settings to the `Career OS Engineering` profile using the verified profile directory. Verify exact JSON content, prohibited-key absence, extension preservation, and Default-profile preservation. Then stop before Step 4.3d.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
