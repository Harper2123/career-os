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

The current subtask is **Step 4.3a: create and verify the empty `Career OS Engineering` profile**.

Do not install extensions, edit profile settings, change Settings Sync, associate the profile with a workspace, alter the Default profile, or begin Step 4.4 during Step 4.3a.

## Definition of done for Step 4.3a

Step 4.3a is complete only when:

- a persistent profile named `Career OS Engineering` exists;
- it was created as an Empty Profile rather than copied from Default or a template;
- it is the selected profile for the verification window;
- it contains zero user-installed extensions before the approved baseline is added;
- the Default profile still exists;
- the Default profile settings file remains unchanged from the Step 4.1 baseline;
- Settings Sync remains unchanged;
- no folder or workspace association has been created yet.

## Verified Step 4.1 inventory

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Only the `Default` profile existed before Step 4.3.
- Installed Default-profile user-extension count: `36`.
- Default-profile `settings.json` existed with SHA-256 `C285A4C03C5727E6A0B1D1B8C65C3371E74F467FD027C559A9CBFFF6A4F7FE28`.
- `keybindings.json` was absent.
- The snippets directory contained zero files.

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

## Approved Step 4.2 architecture

The governing standard is `standards/vscode-environment.md`.

### Profile

Create one dedicated Empty Profile named:

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

## Step 4.3 staged implementation

1. **Step 4.3a:** create and verify the empty profile.
2. **Step 4.3b:** install and verify the approved direct extension baseline in that profile.
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

No technical blocker is known. Step 4.3a requires the user to create the approved Empty Profile and return verification evidence.

## Next action

Create `Career OS Engineering` as an Empty Profile using the approved Windows steps. Verify that it contains zero user-installed extensions and that the Default profile settings remain unchanged. Then stop before installing extensions or editing settings.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
