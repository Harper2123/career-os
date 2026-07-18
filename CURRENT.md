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

**Step 4.3 is complete.**

Step 4.4 has not been authorised.

Do not open a WSL workspace for Step 4 validation, change profile settings, change extensions, change Settings Sync, create profile associations, alter interpreters, tests, terminals, keybindings, or Copilot controls until Ayush explicitly says:

```text
Proceed to Step 4.4
```

## Step 4.3 completion result

The final Windows-side checkpoint passed:

```text
step_4_3e_windows_profile_checkpoint=PASS
```

Visual confirmation also established that:

- `Career OS Engineering` was visibly selected;
- the window was folderless;
- the lower-left indicator showed neither WSL nor Dev Container;
- no setting, extension, profile option, or Settings Sync state was changed during the visual check.

## Verified Windows profile state

### Profile identity

- Visible profile name: `Career OS Engineering`.
- Created from `Empty Profile`, not Default or a template.
- Persistent profile directory ID: `-639a60a5`.
- It is the only non-default profile directory.
- The Default profile remains present.
- Settings Sync was not changed.
- No folder or workspace association exists.

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

- Career OS extension membership is exactly the approved `15` entries;
- Default extension membership remains `36`;
- unexpected extension count is `0`;
- excluded extension count is `0`;
- Career OS and Default extension membership remained unchanged during final verification.

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
- the exact Career OS top-level setting set passed;
- the Python block contains only the Ruff formatter and format-on-save settings.

### Automatic AI boundary

The five approved safety settings are applied to both Default and Career OS Engineering:

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

Verification:

- both profiles contain the exact wildcard-only `github.copilot.enable` map;
- generic inline suggestions are disabled;
- next-edit suggestions are disabled;
- automatic rename suggestions are disabled;
- automatic AI code actions are disabled;
- `chat.disableAIFeatures` remains unset in both profiles;
- manual chat is not globally removed;
- no prohibited interpreter, test, terminal, or Ruff setting appeared.

### Current settings hashes

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

Both hashes matched their Step 4.3d baselines and remained unchanged during final verification.

### Preserved Default-profile state

Known legacy settings remain:

- `editor.formatOnSave=true`;
- `git.autofetch=true`;
- `git.confirmSync=false`;
- `python.defaultInterpreterPath="c:\\msys64\\ucrt64\\bin\\python.exe"`.

The Default profile was preserved rather than cleaned or copied.

## Step 4.3 substep status

1. **Step 4.3a: complete.** Create and verify the Empty Profile.
2. **Step 4.3b: complete.** Install and verify the approved extension baseline.
3. **Step 4.3c: complete.** Apply and verify the minimum non-AI profile settings.
4. **Step 4.3d: complete.** Apply and verify the automatic AI boundary across both profiles.
5. **Step 4.3e: complete.** Run the final Windows-side profile verification and record the checkpoint.

## Step 4.4 scope, awaiting approval

When authorised, Step 4.4 will open a harmless WSL workspace with the `Career OS Engineering` profile and verify:

- profile continuity in a WSL window;
- extension placement and active remote extension scope;
- Linux terminal context;
- WSL remote settings;
- interpreter boundaries;
- no activation of unrelated remote extension families;
- no manual deletion of remote extension directories.

Step 4.4 must preserve the verified Windows-side profile checkpoint.

## Verified Windows and WSL baseline

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Built-in package `GitHub.copilot-chat` version `0.57.0` is present.

### WSL client state before Step 4.4

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

No technical blocker is known. The only blocker is the explicit workflow gate for Step 4.4.

## Next action

Wait for explicit approval:

```text
Proceed to Step 4.4
```

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
