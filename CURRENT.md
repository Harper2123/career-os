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

**Steps 4.1 and 4.2 are complete. Step 4.3 awaits explicit approval.**

Step 4.1 inventoried the current Windows and WSL VS Code state without changing configuration.

Step 4.2 defined the approved profile, extension, interpreter, settings, notebook, Git, and AI-boundary architecture in `standards/vscode-environment.md`.

Do not create the profile, install or disable extensions, edit settings, switch profile associations, or apply the AI boundary until the exact instruction `Proceed to Step 4.3` is given.

## Step 4.1 inventory result

### Windows client

- VS Code version: `1.127.0`, x64.
- CLI command: `C:\Users\akcoo\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd`.
- Only the `Default` profile exists and is selected.
- Installed user-extension count: `36`.
- `settings.json` exists.
- `keybindings.json` is absent.
- The snippets directory contains zero files.
- Inventory and clarification commands left settings, profiles, keybindings, and user-extension directories unchanged.

### Current Windows settings requiring correction

- `python.defaultInterpreterPath="c:\\msys64\\ucrt64\\bin\\python.exe"` exists in the Default profile.
- `github.copilot.enable` enables Python and plaintext despite disabling the general wildcard.
- `github.copilot.nextEditSuggestions.enabled=true`.
- `editor.inlineSuggest.enabled` is not explicitly set.
- The required automatic AI completion boundary is not currently satisfied.

### Built-in Copilot component

- `code --locate-extension github.copilot` returned no location.
- `code --locate-extension github.copilot-chat` located the built-in component under the versioned VS Code installation directory.
- Package ID: `GitHub.copilot-chat`.
- Package version: `0.57.0`.
- The bottom-right status area shows `GitHub Copilot Free`.

### WSL VS Code Server

- WSL user: `akcoo`, UID/GID `1000:1000`.
- Distribution: Ubuntu.
- Server root: `/home/akcoo/.vscode-server`, owned by `akcoo:akcoo`.
- Server version: `1.127.0`.
- Server commit: `4fe60c8b1cdac1c4c174f2fb180d0d758272d713`.
- The server matches the Windows client.
- Actual stopped-server check found zero VS Code Server processes.

### WSL extensions and settings

- Remote extension registry count: `32`.
- No remote GitHub Copilot extension is registered.
- WSL machine settings exist.
- WSL remote user settings are absent.
- `python.defaultInterpreterPath="/bin/python3"` is present at WSL machine scope.
- Copilot, inline-suggestion, and Python test settings are not explicitly set in WSL machine settings.
- Remote extension directories and settings remained unchanged during inventory.

## Step 4.2 approved architecture

The governing standard is `standards/vscode-environment.md`.

### Profile

Create one dedicated Empty Profile named:

```text
Career OS Engineering
```

Do not copy the Default profile. Preserve the Default profile and its installed tools.

Associate the Career OS profile only with relevant WSL repositories, normally under `/home/akcoo/projects`.

Do not change Settings Sync in Career OS v1.

### Direct baseline extensions

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

Install from the Windows client with the Career OS Engineering profile active and allow VS Code to select the correct local or remote extension host.

### Accepted supporting extensions

These may be installed as dependencies or companions:

```text
ms-python.vscode-pylance
ms-python.debugpy
ms-python.vscode-python-envs
ms-toolsai.jupyter-keymap
ms-toolsai.jupyter-renderers
ms-toolsai.vscode-jupyter-cell-tags
ms-toolsai.vscode-jupyter-slideshow
```

Do not treat their presence as permission to expand the baseline further.

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

### Python interpreter boundary

- No Windows Python interpreter is configured in the Career OS Engineering profile.
- Ubuntu `/bin/python3` remains diagnostic and receives no project dependencies.
- Substantial project interpreters and dependencies come from repository-owned Dev Containers.
- No global test framework is selected. Each repository owns its test configuration.

### Automatic AI boundary

Use this target configuration:

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

Manual chat may remain available only when deliberately invoked after a first attempt. Do not set `chat.disableAIFeatures=true` in v1.

Where VS Code supports Apply Setting to all Profiles, apply the automatic AI safety settings across profiles so the Default profile cannot silently restore automatic suggestions.

### Minimum editor settings

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

Do not set a terminal profile unless validation shows that normal WSL bash selection is incorrect.

Do not add global Ruff rules. Project rules belong in repository-owned configuration such as `pyproject.toml`.

### Change policy

- Prefer profile isolation over uninstalling extensions.
- Do not delete extension directories, VS Code Server directories, profile directories, or versioned installation directories.
- Existing unused remote extensions may remain on disk if inactive and non-conflicting.
- Uninstall only after dependency, scope, rollback, and explicit authorisation checks pass.

## Step 4 completion condition

Step 4 is complete only when all of the following work consistently from Windows VS Code using WSL:

- Python editing and execution through the approved container workflow;
- Jupyter notebooks where justified;
- Markdown editing and preview;
- test discovery and execution;
- Git inspection and operations;
- integrated Linux terminal commands;
- Docker and Dev Container workflows;
- the minimum approved extension and profile set;
- automatic AI completion disabled by default.

## Remaining Step 4 sequence

1. **Step 4.3, Windows profile:** create the Empty Profile, activate the approved baseline, apply minimum settings, and apply the automatic AI boundary.
2. **Step 4.4, WSL profile:** open a harmless WSL workspace, verify extension placement and Linux context, and exclude unrelated remote extensions from the active profile without deleting directories.
3. **Step 4.5, editor workflows:** validate Python, Ruff, Jupyter, Markdown, tests, Git, GitHub pull-request access, and the integrated Linux terminal.
4. **Step 4.6, container workflows:** validate Container Tools and Dev Containers against repository-owned configuration.
5. **Step 4.7, AI boundary:** prove that automatic AI suggestions do not appear while manual chat remains explicitly invoked.
6. **Step 4.8, end-to-end test and cleanup:** run one harmless complete workflow and remove only explicitly disposable artifacts.
7. Review and create one Step 4 pull request only after all checks pass.

Later substeps are not authorised merely by being listed here.

## Governing constraints

- Prefer the minimum useful configuration.
- Do not add extensions merely because they are popular.
- Do not duplicate capabilities already supplied by VS Code, WSL, Docker Desktop, or repository-owned containers.
- Keep automatic AI completion disabled by default.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not install project dependencies into Ubuntu system Python.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.
- Excessive VS Code customisation remains excluded from Career OS v1.

## Immediate blocker

Step 4.3 requires explicit approval. There is no unresolved Step 4.2 design blocker.

## Next action

Wait for the exact instruction `Proceed to Step 4.3` before changing VS Code.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
