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

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The environment must support Python, notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.5 is active.**

**Steps 4.5a and 4.5b are complete.**

The current execution unit remains **Step 4.5c: consolidated editor-workflow validation and focused recovery**.

The first Step 4.5c run produced a partial pass:

```text
step_4_5c_live_context=PASS
live_unittest_execution=PASS
step_4_5c_live_restore=PASS
```

Verified live state:

- fixture opened in Ubuntu WSL;
- integrated terminal used Bash in the exact fixture root;
- Git remained on `main`, one commit, clean worktree, zero remotes;
- the accepted fixture commit and tree hash were preserved;
- dependency-free unittest passed from the terminal;
- no remote, push, validation commit, or package installation occurred.

The editor workflow did not pass:

- Ruff produced no diagnostic;
- Ruff format-on-save did not change the intentionally unformatted Python file, confirmed by an empty editor-generated diff;
- markdownlint produced no diagnostic;
- the Testing beaker view was absent;
- the final Ubuntu preservation script stopped because Windows executable interoperability had again disappeared and `powershell.exe` returned `Exec format error`.

The combined evidence indicates that the Python, Ruff, and markdownlint extensions are not active in the Ubuntu WSL extension host for this profile, despite their packages being present in extension storage. VS Code remote development runs workspace extensions in the remote extension host, so local profile membership alone is insufficient for these features.

A focused correction is authorised inside Step 4.5c:

- install or enable only `ms-python.python`, `charliermarsh.ruff`, and `davidanson.vscode-markdownlint` in `WSL: Ubuntu` for the active `Career OS Engineering` profile;
- allow the Python extension's required supporting extensions to activate automatically;
- do not install global host CLIs or Python packages;
- do not add unrelated extensions;
- re-run the Python, Ruff, Markdown, Testing, Source Control, and preservation checks in one session.

The recurring WSL-to-Windows executable interop loss is now classified as a known non-blocking host defect for Step 4.5. Windows process checks must run from Windows PowerShell, and Ubuntu preservation checks must not depend on launching Windows executables. No manual `binfmt_misc` service or persistent workaround is authorised during Step 4.

## Remaining Step 4 execution model

To avoid prolonged setup work, the remaining Step 4 plan is consolidated into three execution units:

1. **Step 4.5c: active.** Focused remote-extension correction, editor-workflow validation, and preservation.
2. **Step 4.6:** consolidated Container Tools, Dev Container, Python runtime, notebook-when-justified, and container end-to-end validation.
3. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance review, pull request, merge, and branch cleanup. This absorbs the former Step 4.8 final checkpoint.

Later units remain gated and are not authorised merely by being listed.

## Accepted VS Code baseline

- Profile: `Career OS Engineering`
- Persistent profile directory ID: `-639a60a5`
- Career OS local extension membership: exactly `15`
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
WSL extension registry hash before focused correction: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash before focused correction: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash before focused correction: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
```

Additional verified state:

- Ubuntu `24.04.2 LTS` on WSL2
- User `akcoo`, UID/GID `1000:1000`
- Workspace filesystem `ext4`
- Ubuntu diagnostic Python `3.12.3` at `/bin/python3`
- No active virtual environment, Conda environment, or `PYTHONPATH`
- No user-installed Copilot package in the WSL registry
- Twenty excluded extension packages remain stored but inactive

## Disposable fixture checkpoint

```text
Path: /home/akcoo/projects/career-os-vscode-wsl-check
Fixture commit: b83b3b72e5934b69b81bd46890301d5ba22c7ec5
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

- the fixture opens using `Career OS Engineering` in Ubuntu WSL, not a Dev Container;
- the integrated terminal starts in the fixture root using Bash;
- Python language navigation or hover works;
- Ruff reports the intentional unused import and format-on-save reformats the spacing case;
- built-in Markdown preview renders the README;
- markdownlint reports the intentional heading-level diagnostic;
- VS Code discovers and passes the one unittest test;
- Source Control shows the temporary formatting diff;
- GitHub Pull Requests view opens without creating anything;
- the fixture returns exactly to the accepted commit, tree hash, clean worktree, one commit, and zero remotes;
- only the demonstrated WSL remote-extension activation change occurs;
- Windows VS Code and the WSL Server stop normally;
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
- Preserve the Step 3 host, WSL, Docker, and interoperability architecture where practical.
- Do not add a persistent WSL interop repair during Step 4.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

The Python, Ruff, and markdownlint workspace extensions are not active in the Ubuntu WSL extension host for the active profile.

The next action is the focused Step 4.5c remote-extension correction and re-validation. Step 4.6 remains blocked until this evidence is reviewed.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private