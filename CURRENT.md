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

**Step 4.5 is active.**

**Steps 4.5a and 4.5b are complete.** The current subtask is **Step 4.5c: open the disposable fixture through Windows VS Code using `Career OS Engineering` and Ubuntu WSL, then verify profile continuity and terminal context**.

Until Step 4.5c instructions are given:

- keep Windows VS Code closed;
- keep Docker Desktop stopped;
- do not edit the fixture;
- do not run the WSL `code` command;
- do not add a Git remote or push;
- do not install packages or Python dependencies;
- do not change extensions, settings, interpreters, tests, terminals, profiles, Settings Sync, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 4.6 or Step 5.

## Step 4 implementation status

1. **Step 4.1: complete.** Inventory the existing Windows and WSL VS Code state.
2. **Step 4.2: complete.** Define the minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Create and verify the Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** Validate WSL profile continuity, extension scope, terminal context, settings, interpreter boundaries, and closed-window preservation.
5. **Step 4.5: active.** Validate editor workflows for Python, Ruff, Markdown, tests, Git, GitHub pull requests, and the integrated terminal.
6. **Step 4.6:** validate Container Tools and repository-owned Dev Containers.
7. **Step 4.7:** verify the automatic AI boundary end to end.
8. **Step 4.8:** run the final harmless end-to-end workflow and remove only explicitly disposable artifacts.

Later steps are not authorised merely by being listed.

## Step 4.5 objective

Validate the minimum editor workflows without weakening the container-first runtime policy.

Step 4.5 uses the disposable workspace:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

The fixture is a small local Git repository containing only harmless smoke-test files. It will not be pushed, published, connected to a remote, or treated as a portfolio project.

Ubuntu system Python may be used only for a dependency-free, standard-library smoke check. No project dependency may be installed into Ubuntu system Python. Substantial runtime validation remains reserved for the repository-owned Dev Container in Step 4.6.

## Step 4.5 staged sequence

1. **Step 4.5a: complete.** Closed-editor preflight and controlled interoperability recovery.
2. **Step 4.5b: complete.** Create and verify the disposable local Git fixture with minimal Python, unittest, Markdown, project Ruff configuration, and repository-local VS Code test settings.
3. **Step 4.5c: active.** Open the fixture through Windows VS Code using `Career OS Engineering` and Ubuntu WSL, then verify profile continuity and terminal context.
4. **Step 4.5d:** validate Python editing, language support, Ruff diagnostics, and format-on-save.
5. **Step 4.5e:** validate Markdown editing, built-in preview, and markdownlint diagnostics.
6. **Step 4.5f:** validate unittest discovery and execution through VS Code using only the dependency-free host smoke fixture.
7. **Step 4.5g:** validate built-in Source Control inspection and GitHub Pull Requests access without pushing, creating a pull request, or changing the public repository.
8. **Step 4.5h:** run the final editor-workflow preservation checkpoint and leave cleanup for the explicitly authorised later step.

Each substep begins only after the previous substep's evidence is reviewed.

## Step 4.3 Windows profile checkpoint

Verified state:

- profile name `Career OS Engineering`;
- persistent profile directory ID `-639a60a5`;
- Career OS extension membership exactly `15`;
- Default extension membership `36`;
- no Windows Python interpreter, global test framework, terminal profile, Ruff rule configuration, or keybindings in the Career OS profile;
- five automatic-AI safety settings disabled across Default and Career OS profiles;
- `chat.disableAIFeatures` unset;
- Settings Sync unchanged.

Verified settings hashes:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

## Step 4.4 WSL checkpoint

Overall result:

```text
step_4_4_wsl_profile_validation=PASS
```

Accepted client and WSL Server state:

```text
VS Code version: 1.129.1
Client and WSL Server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
```

Accepted WSL baselines:

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
```

Additional verified WSL state:

- Ubuntu `24.04.2 LTS` on WSL2;
- user `akcoo`, UID/GID `1000:1000`;
- workspace owner `akcoo:akcoo`, mode `755`, filesystem `ext4`;
- no active virtual environment, Conda environment, or `PYTHONPATH`;
- `/bin/python3` is Ubuntu diagnostic Python `3.12.3`;
- WSL machine setting remains `python.defaultInterpreterPath="/bin/python3"`;
- WSL user-extension registry contains `32` entries and no Copilot package;
- twenty excluded extension packages remain stored but inactive.

## Step 4.5a completion result

The controlled WSL interoperability recovery and revised closed-editor preflight passed:

```text
interop_classification=HEALTHY_AFTER_CONTROLLED_RESTART
step_4_5a_post_restart_interop=PASS
step_4_5a_closed_editor_preflight=PASS
```

Verified:

- Windows VS Code and the Ubuntu VS Code Server were stopped;
- Windows executable interoperability was healthy;
- the workspace was empty and not a Git repository;
- Git `2.43.0` and the expected global identity were present;
- Ubuntu Python `3.12.3` and standard-library `unittest` were available;
- no virtual environment, Conda environment, or `PYTHONPATH` was active;
- Ruff, `markdownlint`, and `markdownlint-cli2` host CLIs were absent, which was accepted;
- no package installation or protected-state change occurred.

## Step 4.5b completion result

The disposable fixture creation passed:

```text
step_4_5b_disposable_fixture=PASS
```

Fixture contents:

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

Verified:

- exact file count `9` and exact directory count `3` before Git initialisation;
- workspace-local unittest settings enable unittest and disable pytest;
- no workspace interpreter setting exists;
- repository-local Ruff and markdownlint configurations exist;
- one intentional Ruff diagnostic, one intentional formatting case, and one intentional markdownlint diagnostic remain for later editor validation;
- Python syntax passed for four Python files;
- the fixture privacy boundary passed;
- dependency-free unittest execution passed with one test;
- local Git branch `main`;
- one clean commit;
- no Git remote;
- no push;
- approved Git author identity;
- protected Windows and WSL baselines remained unchanged;
- Docker Desktop remained stopped and VS Code remained closed.

Accepted local fixture checkpoint:

```text
Commit: b83b3b72e5934b69b81bd46890301d5ba22c7ec5
Subject: test: create disposable editor workflow fixture
Fixture tree hash: 0c07de1958c5d7fc8a8a48b25a0995f48f22ae4483a3bb193ef7cb71de132a42
Tracked files: 9
Git remotes: 0
```

## Remaining Step 4 work

Currently named remaining work:

- six Step 4.5 substeps: `4.5c` through `4.5h`;
- three later Step 4 units: `4.6`, `4.7`, and `4.8`;
- one final Step 4 pull request, review, merge, and branch cleanup checkpoint after all Step 4 validation passes.

The later units may be divided into smaller execution substeps when each one becomes active.

## Definition of done for Step 4.5c

Step 4.5c is complete only when evidence proves:

- the fixture opens from Windows VS Code using the `Career OS Engineering` profile and Ubuntu WSL context;
- the exact workspace path is `/home/akcoo/projects/career-os-vscode-wsl-check`;
- the active profile remains `Career OS Engineering`;
- the remote status remains Ubuntu WSL and not a Dev Container;
- the integrated terminal starts in the fixture root using Bash;
- Git branch `main`, clean worktree, one commit, and zero remotes remain visible and unchanged;
- no extension, setting, interpreter, package, remote, push, or fixture edit occurs;
- Docker Desktop remains stopped;
- the WSL `code` command is not invoked.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Do not manually register `binfmt_misc` handlers or add a persistent repair service.
- Do not edit `/etc/wsl.conf` or `.wslconfig` without new evidence that the normal restart path no longer works.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not install packages or project dependencies into Ubuntu system Python.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve the Step 3 host, WSL, Docker, and Windows interoperability architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known.

Step 4.5c is the next authorised substep. Step 4.5d remains blocked until Step 4.5c evidence is reviewed.

## Next action

Keep Docker Desktop stopped. Follow the Step 4.5c instructions from the active setup conversation. Stop before editing fixture files or beginning Python workflow validation.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.