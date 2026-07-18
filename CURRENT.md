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

The environment must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.5 is active.**

**Steps 4.5a and 4.5b are complete.**

The current execution unit is **Step 4.5c: consolidated editor-workflow validation**.

Ayush explicitly authorised combining the former Step 4.5c through Step 4.5h checks into one coherent unit so environment setup does not crowd out MScFE work. This unit covers:

- opening the fixture through Windows VS Code with `Career OS Engineering` and Ubuntu WSL;
- integrated Bash terminal context;
- Python language support;
- Ruff diagnostics and format-on-save;
- Markdown preview and markdownlint diagnostics;
- unittest discovery and execution;
- built-in Source Control inspection;
- GitHub Pull Requests view access without creating anything;
- restoration of the disposable fixture to its accepted clean baseline;
- final closed-window preservation.

During this unit:

- keep Docker Desktop stopped;
- do not run the WSL `code` command;
- do not install packages or Python dependencies;
- do not add a Git remote or push;
- do not commit validation edits;
- do not change profile, user, machine, extension, Settings Sync, terminal, Copilot, or container settings;
- do not open a Dev Container;
- do not begin the next consolidated Step 4 unit until this evidence is reviewed.

## Remaining Step 4 execution model

To avoid prolonged setup work, the remaining Step 4 plan is consolidated into three execution units:

1. **Step 4.5c: active.** Consolidated editor-workflow validation and preservation.
2. **Step 4.6:** consolidated Container Tools, Dev Container, Python runtime, notebook-when-justified, and container end-to-end validation.
3. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, Step 4 acceptance review, pull request, merge, and branch cleanup. This absorbs the former Step 4.8 final checkpoint.

Later units remain gated and are not authorised merely by being listed.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: active.** Editor workflows.
6. **Step 4.6:** consolidated container workflow.
7. **Step 4.7:** consolidated AI boundary and final Step 4 closure.

## Accepted VS Code baseline

- Profile: `Career OS Engineering`
- Persistent profile directory ID: `-639a60a5`
- Career OS extension membership: exactly `15`
- Default extension membership: `36`
- No Windows Python interpreter in the Career OS profile
- No global test framework, terminal profile, Ruff rule configuration, or keybindings
- Automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions disabled
- `chat.disableAIFeatures` unset so deliberate manual chat remains available
- Settings Sync unchanged

Settings hashes:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

## Accepted WSL baseline

```text
VS Code and WSL Server version: 1.129.1
Client and server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
```

Additional verified state:

- Ubuntu `24.04.2 LTS` on WSL2
- User `akcoo`, UID/GID `1000:1000`
- Workspace filesystem `ext4`
- Ubuntu diagnostic Python `3.12.3` at `/bin/python3`
- No active virtual environment, Conda environment, or `PYTHONPATH`
- WSL user-extension registry contains `32` entries and no Copilot package
- Twenty excluded extension packages remain stored but inactive
- Windows executable interoperability restored by a controlled WSL restart

## Step 4.5a result

```text
interop_classification=HEALTHY_AFTER_CONTROLLED_RESTART
step_4_5a_post_restart_interop=PASS
step_4_5a_closed_editor_preflight=PASS
```

Git `2.43.0`, the expected global identity, diagnostic Python, and standard-library unittest are available. Ruff, `markdownlint`, and `markdownlint-cli2` host CLIs are absent, which is accepted because Step 4 validates their VS Code extensions rather than installing global host tools.

## Step 4.5b fixture checkpoint

Disposable local fixture:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

Tracked files:

```text
.gitignore
.markdownlint.json
.vscode/settings.json
README.md
career_os_smoke/__init__.py
career_os_smoke/arithmetic.py
pyproject.toml
tests/__init__.py
tests/test_arithmetic.py
```

Accepted state:

```text
Fixture commit: b83b3b72e5934b69b81bd46890301d5ba22c7ec5
Subject: test: create disposable editor workflow fixture
Fixture tree hash: 0c07de1958c5d7fc8a8a48b25a0995f48f22ae4483a3bb193ef7cb71de132a42
Branch: main
Commit count: 1
Tracked files: 9
Git remotes: 0
Worktree: clean
```

The fixture contains one intentional Ruff diagnostic, one intentional formatting case, and one intentional markdownlint diagnostic. Its workspace settings enable unittest, disable pytest, and do not set a project interpreter.

## Definition of done for consolidated Step 4.5c

The unit is complete only when evidence proves:

- Windows VS Code opens the fixture using `Career OS Engineering` and Ubuntu WSL;
- the remote context is Ubuntu WSL, not a Dev Container;
- the integrated terminal starts in the fixture root using Bash;
- Python language navigation or hover works;
- Ruff reports the intentional unused import;
- Ruff format-on-save reformats the intentional spacing case without removing the unused import;
- built-in Markdown preview renders the README;
- markdownlint reports the intentional heading-level diagnostic;
- VS Code discovers and passes the one unittest test;
- built-in Source Control shows the temporary formatting edit and its diff;
- GitHub Pull Requests view opens without creating a remote, pull request, issue, or external change;
- the temporary editor edit is restored to `HEAD`;
- the fixture returns exactly to the accepted commit, tree hash, clean worktree, one commit, and zero remotes;
- protected Windows and WSL settings and extension baselines remain unchanged;
- VS Code and the WSL Server stop normally at the final closed-window checkpoint;
- Docker Desktop remains stopped;
- no package, dependency, remote, push, commit, or public action occurs.

## MScFE state

- Completed courses: Financial Markets, Financial Data, Financial Econometrics
- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, course work, and recovery take priority over optional setup or personal engineering work
- Once the course begins, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week
- No guilt debt applies to unfinished setup work

## Governing constraints

- Prefer the minimum reliable configuration over completeness for its own sake.
- Preserve the Default profile and existing tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not install project dependencies into Ubuntu system Python.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Preserve the Step 3 host, WSL, Docker, and interoperability architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known.

The next action is the consolidated Step 4.5c editor-workflow validation. Step 4.6 remains blocked until this evidence is reviewed.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
