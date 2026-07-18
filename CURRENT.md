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

The environment must support Python, notebooks where justified, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.5 is complete.**

The next gated unit is **Step 4.6: consolidated Container Tools, Dev Container, Python runtime, notebook-when-justified, and container end-to-end validation**.

Step 4.6 has not started and requires Ayush to say:

```text
Proceed to Step 4.6
```

Until then:

- keep Docker Desktop stopped;
- keep VS Code closed;
- do not edit or delete the disposable fixture;
- do not run the WSL `code` command;
- do not install packages or dependencies;
- do not change extensions, profiles, settings, interpreters, terminals, Settings Sync, or Copilot controls;
- do not add a Git remote, push, or create a validation commit;
- do not begin Step 4.7 or Step 5.

## Remaining Step 4 execution model

To avoid prolonged setup work, the remaining Step 4 plan is consolidated into two execution units:

1. **Step 4.6:** consolidated Container Tools, Dev Container, Python runtime, notebook-when-justified, and container end-to-end validation.
2. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance review, pull request, merge, and branch cleanup. This absorbs the former Step 4.8 final checkpoint.

Later units remain gated and are not authorised merely by being listed.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6:** consolidated container workflow.
7. **Step 4.7:** consolidated AI boundary and final Step 4 closure.

## Accepted Windows VS Code baseline

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

## Accepted WSL baseline after Step 4.5

```text
VS Code and WSL Server version: 1.129.1
Client and server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

Additional accepted state:

- Ubuntu `24.04.2 LTS` on WSL2
- User `akcoo`, UID/GID `1000:1000`
- Workspace filesystem `ext4`
- Ubuntu diagnostic Python `3.12.3` at `/bin/python3`
- No active virtual environment, Conda environment, or `PYTHONPATH`
- Global WSL extension registry contains `32` entries
- Career OS WSL profile registry contains `7` entries
- No user-installed Copilot entry exists in any WSL extension registry
- Python, Ruff, and markdownlint are present in the Career OS WSL profile registry
- Ruff and Python are also present in the global WSL registry
- markdownlint is profile-scoped and absent from the global WSL registry
- One remote package directory exists for each of Python, Ruff, and markdownlint
- Twenty previously excluded extension packages may remain stored but inactive

## Disposable fixture checkpoint

```text
Path: /home/akcoo/projects/career-os-vscode-wsl-check
Fixture commit: b83b3b72e5934b69b81bd46890301d5ba22c7ec5
Subject: test: create disposable editor workflow fixture
Fixture tree hash: 0c07de1958c5d7fc8a8a48b25a0995f48f22ae4483a3bb193ef7cb71de132a42
Branch: main
Commit count: 1
Tracked files: 9
Git remotes: 0
Worktree: clean
```

The fixture remains local-only and must not be pushed or treated as a portfolio project.

## Step 4.5 completion evidence

### Live context

```text
step_4_5c_live_context=PASS
```

Verified exact fixture path, Bash integrated terminal, Ubuntu WSL context, branch `main`, accepted fixture commit, one commit, clean worktree, and zero remotes.

### Editor workflow

Verified functionally:

- Python language navigation and hover worked;
- Ruff reported the intentional unused-import diagnostic;
- Ruff format-on-save produced exactly the intended spacing-only diff;
- markdownlint reported the intentional heading-level diagnostic;
- built-in Markdown preview rendered correctly;
- the Testing beaker appeared;
- VS Code discovered and passed the one unittest test;
- Source Control displayed the expected temporary formatting diff;
- GitHub Pull Requests view opened but remained at `Loading` for the no-remote fixture, accepted as a limited local-fixture result.

The editor-generated diff was exactly:

```diff
-def add(left:int,right:int)->int:
-    return left+right
+def add(left: int, right: int) -> int:
+    return left + right
```

### Fixture restoration

```text
git_head_check=PASS
git_commit_count_check=PASS
git_clean_worktree_check=PASS
git_remote_count_check=PASS
tracked_file_count_check=PASS
fixture_tree_hash_check=PASS
step_4_5c_editor_recovery=PASS
```

### Closed-window preservation

```text
windows_code_process_check=PASS
step_4_5c_windows_closed=PASS
vscode_server_process_count_check=PASS
machine_settings_hash_check=PASS
remote_user_settings_hash_check=PASS
default_settings_hash_check=PASS
career_settings_hash_check=PASS
registry_parse_check=PASS
all_registry_copilot_check=PASS
extension_scope_inventory=PASS
closed_unittest_execution=PASS
step_4_5c_final_inventory=PASS
```

No package, dependency, Git remote, push, validation commit, extension change during final inventory, or public action occurred. Docker Desktop remained stopped.

## Known host issue

WSL-to-Windows executable interoperability has disappeared more than once during Step 4. A controlled `wsl --shutdown` restored it temporarily, but the failure later recurred.

Operational rule for the remainder of Step 4:

- perform Windows process checks from Windows PowerShell;
- keep Ubuntu preservation checks Linux-only;
- do not add a persistent `binfmt_misc` service, manual handler, or WSL configuration workaround during Step 4;
- record and review the defect during final Step 4 acceptance.

This issue does not block editor or container work unless a later required workflow specifically depends on launching a Windows executable from Ubuntu.

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
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known.

Step 4.6 remains blocked only by the explicit approval gate.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
