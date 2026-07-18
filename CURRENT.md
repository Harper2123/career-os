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

Step 4.3a is complete. The current subtask is **Step 4.3b: install and verify the approved direct extension baseline in the `Career OS Engineering` profile**.

During Step 4.3b, do not edit profile settings, change Settings Sync, associate the profile with a folder or workspace, alter the Default profile, change Copilot settings, configure Python, or begin Step 4.4.

## Step 4.3a result

The approved empty profile was created and verified:

- visible profile name: `Career OS Engineering`;
- created from `Empty Profile`, not Default or a template;
- `Career OS Engineering` was selected for the verification window;
- `Default` remained visible;
- Settings Sync was not changed;
- persistent profile directory ID: `-639a60a5`;
- the profile directory contained only `globalStorage/state.vscdb` and its backup;
- Career OS profile user-extension count: `0`;
- Default profile user-extension count remained `36`;
- Default profile `settings.json` SHA-256 remained `C285A4C03C5727E6A0B1D1B8C65C3371E74F467FD027C559A9CBFFF6A4F7FE28`;
- Default profile `keybindings.json` remained absent;
- result: `step_4_3a_empty_profile=PASS`.

No extension was installed and no setting was edited during Step 4.3a.

## Definition of done for Step 4.3b

Step 4.3b is complete only when:

- all eight approved direct extensions belong to the `Career OS Engineering` profile;
- only accepted supporting extensions are added automatically as dependencies or companions;
- excluded extension families are not activated in the profile;
- the Default profile still exists with the same extension membership count;
- no profile settings, Settings Sync state, workspace association, interpreter, test framework, or Copilot setting is changed;
- the final profile extension inventory is recorded and verified.

## Approved Step 4.2 architecture

The governing standard is `standards/vscode-environment.md`.

### Profile

Use one dedicated Empty Profile named:

```text
Career OS Engineering
```

Preserve the Default profile. Do not copy it. Do not change Settings Sync in Career OS v1.

### Direct extension baseline

```text
ms-vscode-remote.remote-wsl
ms-vscode-remote.remote-containers
ms-azuretools.vscode-containers
github.vscode-pull-request-github
ms-python.python
charliermarsh.ruff
ms-toolsai.jupyter
davidanson.vscode-markdownlint
```

Install these for the `Career OS Engineering` profile from the Windows VS Code client or the profile-aware Windows CLI. Allow VS Code to place extension code in the appropriate local, WSL, or container extension host later.

### Accepted supporting extensions

The following may appear as dependencies or companions:

```text
ms-python.vscode-pylance
ms-python.debugpy
ms-python.vscode-python-envs
ms-toolsai.jupyter-keymap
ms-toolsai.jupyter-renderers
ms-toolsai.vscode-jupyter-cell-tags
ms-toolsai.vscode-jupyter-slideshow
```

Their presence is not permission to expand the direct baseline.

### Baseline exclusions

The Career OS Engineering profile does not activate unrelated or overlapping extension families by default, including:

- third-party Python extension packs and environment managers;
- C, C++, and CMake tooling;
- Django and Jinja tooling;
- GitLens;
- IntelliCode and automatic AI suggestion extensions;
- enhanced or overlapping Markdown extensions;
- decorative theme, icon, comment, and indentation extensions;
- CSV, path-completion, and docstring helpers;
- the legacy Docker extension pack.

Use built-in Git Source Control and Markdown preview. Use `ms-azuretools.vscode-containers` rather than the older `ms-azuretools.vscode-docker` pack.

### Runtime boundary

- Do not configure a Windows Python interpreter in the Career OS profile.
- Ubuntu system Python remains diagnostic and receives no project dependencies.
- Substantial Python projects use repository-owned Dev Containers.
- Each repository owns its test configuration.

### Automatic AI target

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

## Verified Step 4.1 inventory

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Installed Default-profile user-extension count before Step 4.3: `36`.
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
2. **Step 4.3b: active.** Install and verify the approved direct extension baseline in that profile.
3. **Step 4.3c:** apply and verify the minimum profile settings.
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

No technical blocker is known. Step 4.3b requires installing the approved direct baseline only for `Career OS Engineering` and returning verification evidence.

## Next action

Install the approved direct extension baseline for `Career OS Engineering` using the profile-aware Windows CLI. Verify the resulting profile inventory and Default-profile preservation. Then stop before editing settings.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
