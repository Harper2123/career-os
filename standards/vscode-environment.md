# VS Code Environment Standard

## Purpose

This document defines the minimum Visual Studio Code architecture for Career OS on Windows using Ubuntu WSL and repository-owned development containers.

The goal is a reliable engineering control centre, not a heavily customised editor.

## Architectural decision

Use one dedicated VS Code profile named:

```text
Career OS Engineering
```

Create it as an Empty Profile rather than copying the existing Default profile.

The Default profile remains preserved. Existing extensions and settings outside the Career OS profile are not removed merely to make the installation look clean.

Associate the Career OS profile only with relevant folders and workspaces, normally repositories under:

```text
/home/akcoo/projects
```

Do not change Settings Sync during Career OS v1 unless a demonstrated need justifies it.

## Why an Empty Profile

The current Default profile contains useful tools mixed with unrelated extension families, legacy helpers, cosmetic extensions, and automatic AI settings.

Starting from an Empty Profile provides:

- a known active extension set;
- no inherited Windows MSYS2 Python interpreter path;
- no inherited automatic Copilot completion settings;
- no need to uninstall tools that may still be useful outside Career OS;
- simpler verification and recovery.

## Extension architecture

### Direct baseline extensions

The Career OS Engineering profile uses this direct baseline:

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

Install extensions from the Windows VS Code client while the Career OS Engineering profile is active. Allow VS Code to place each extension in the local, WSL, or container extension host according to its extension kind.

Do not manually duplicate an extension across local and remote hosts unless the Extensions view reports that the remote installation is required.

### Required supporting extensions

The following supporting extensions are accepted when installed as dependencies or companions of the direct baseline:

```text
ms-python.vscode-pylance
ms-python.debugpy
ms-python.vscode-python-envs
ms-toolsai.jupyter-keymap
ms-toolsai.jupyter-renderers
ms-toolsai.vscode-jupyter-cell-tags
ms-toolsai.vscode-jupyter-slideshow
```

Pylance and debugpy are required capabilities for language support and debugging. The Python Environments extension may be present, but it does not change the Career OS container-first environment rule.

Jupyter companion extensions may remain when installed with Jupyter. They are not separate reasons to expand the baseline.

### Built-in capabilities

Use VS Code built-in capabilities where they are sufficient:

- Source Control for normal Git inspection and operations;
- Markdown editing and preview;
- integrated terminal support;
- file navigation, search, and basic language editing;
- settings and workspace management.

### Excluded from the baseline

Do not activate these extension categories in the Career OS Engineering profile unless a real project requires them:

- third-party Python extension packs or environment managers;
- C, C++, or CMake tooling;
- Django or Jinja tooling;
- GitLens;
- IntelliCode or other automatic AI suggestion extensions;
- enhanced Markdown preview or multiple overlapping Markdown workflow extensions;
- decorative comment, indentation, icon, and theme extensions;
- CSV-specific tooling;
- path-completion helpers;
- docstring generators;
- legacy Docker extension packs.

The current `ms-azuretools.vscode-containers` extension is the selected container-management extension. The older `ms-azuretools.vscode-docker` extension pack is not part of the baseline.

An excluded extension may be added later only when an active project demonstrates a concrete need.

## Python and runtime architecture

### Windows

Do not configure a Windows Python interpreter for Career OS engineering work.

The existing Default-profile MSYS2 interpreter path is not copied into the Career OS Engineering profile.

### WSL

Ubuntu system Python may remain available at `/bin/python3` for operating-system diagnostics and lightweight host checks.

Do not install project dependencies into Ubuntu system Python.

### Dev Containers

Substantial Python projects use the interpreter and dependencies defined by the repository-owned container configuration.

The Dev Container should select its container interpreter, normally from the container PATH. A project may add an explicit workspace interpreter setting only when automatic detection is unreliable and the path is stable inside that project's container.

Repository-owned `devcontainer.json` files should declare only the extensions required by that project. Jupyter is added to a project container only when notebook work is justified.

## Settings architecture

### Automatic AI boundary

Automatic AI suggestions are disabled across Career OS engineering work.

Use these settings:

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

Do not set `chat.disableAIFeatures` to `true` in v1. Manual chat may remain available when deliberately invoked after a first attempt. The boundary is against automatic completion, next-edit prediction, automatic rename suggestions, and automatic AI code actions.

Apply the automatic AI boundary consistently to the Career OS Engineering profile. Where VS Code offers Apply Setting to all Profiles, use it for these safety settings so opening the Default profile does not silently restore automatic suggestions.

Current VS Code releases ship GitHub Copilot Chat as a built-in extension. A built-in extension may appear in `Developer: Show Running Extensions` under the WSL extension host even when no user-installed Copilot extension exists in the local or WSL installed-extension inventories. That host placement is not by itself an extension-scope failure. The Career OS acceptance boundary is:

- no user-installed Copilot extension in the Career OS local or WSL installed-extension inventory;
- no Copilot package in the WSL user-extension registry;
- the five automatic AI safety settings remain enforced;
- `chat.disableAIFeatures` remains unset so manual chat is preserved.

Do not disable all AI features merely to force the built-in Copilot Chat process out of a remote extension host.

### Editor and Git settings

Use this minimum profile configuration:

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

Do not define a global Python test framework. Each repository selects pytest or unittest through its own workspace configuration.

Do not define a global Python interpreter path in the Career OS Engineering profile.

Do not change terminal profile settings unless validation shows that the normal WSL bash terminal is not selected correctly.

Do not add global Ruff rule configuration in VS Code. Project rules belong in repository-owned configuration such as `pyproject.toml`.

## Notebook policy

Jupyter is available for justified exploratory, research, and explanatory notebook work.

Notebook kernels and dependencies come from the active repository-owned environment, normally the Dev Container. Do not create a separate global notebook environment merely for VS Code.

Reusable logic still moves from notebooks into Python modules with tests when appropriate.

## Git and GitHub policy

Use built-in Source Control for normal Git operations.

Use GitHub Pull Requests and Issues for pull-request inspection and review from VS Code.

Step 4 validates that these capabilities work. Step 5 defines and practises the full issue, branch, commit, pull-request, review, and merge workflow.

## Change and cleanup policy

Prefer profile isolation over uninstalling extensions from the Default profile.

Do not manually delete extension directories, VS Code Server directories, profile directories, or versioned VS Code installation directories.

Unused remote extensions may remain installed on disk if they are inactive in the Career OS Engineering profile and cause no conflict.

Uninstall an extension only when all of the following are true:

1. it is not a dependency of an approved extension;
2. it is not required by another active profile or project;
3. the exact installation scope is known;
4. removal has a verified rollback path;
5. the removal is explicitly authorised in the active substep.

## Step 4 implementation sequence

### Step 4.3

Create the Empty Profile, add the approved direct baseline, apply the minimum profile settings, and apply the automatic AI boundary. Preserve the Default profile.

### Step 4.4

Open a harmless WSL workspace with the Career OS Engineering profile. Verify extension placement, remote settings, Linux terminal context, and interpreter boundaries. Exclude unrelated remote extensions from the active profile without manually deleting extension directories.

### Step 4.5

Validate Python editing, Ruff formatting, Markdown preview and linting, test discovery, Git inspection, GitHub pull-request access, and the integrated Linux terminal.

### Step 4.6

Validate Container Tools and Dev Containers against a repository-owned container definition.

### Step 4.7

Prove that no automatic Copilot ghost text, next-edit suggestion, automatic rename suggestion, or AI code action appears. Confirm that manual chat remains available only when deliberately invoked.

### Step 4.8

Run one harmless end-to-end workflow and remove only explicitly disposable artifacts.

## Completion condition

Step 4 is complete only when the approved profile and active extension set are verified and the following work consistently from Windows VS Code using WSL:

- Python editing and execution through the approved container workflow;
- Jupyter notebooks where justified;
- Markdown editing and preview;
- test discovery and execution;
- Git inspection and operations;
- integrated Linux terminal commands;
- Docker and Dev Container workflows;
- automatic AI completion disabled by default.
