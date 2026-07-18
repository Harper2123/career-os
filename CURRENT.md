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

The current execution unit remains **Step 4.5c: consolidated editor-workflow validation and final extension-scope inventory**.

The focused editor recovery succeeded functionally:

- Ruff reported the intended unused-import diagnostic;
- Ruff format-on-save produced exactly the intended spacing-only diff;
- markdownlint reported the intended heading-level diagnostic;
- Python language support was available;
- the Testing beaker appeared;
- VS Code discovered and passed the one unittest test;
- Markdown preview rendered correctly;
- Source Control showed the expected temporary diff;
- the fixture was restored to its accepted clean baseline;
- Windows VS Code closed normally;
- Docker Desktop remained stopped;
- no remote, push, validation commit, package installation, or public action occurred.

The GitHub Pull Requests view opened but remained at `Loading`. This is accepted as a limited no-remote fixture result. Actual pull-request creation and review will occur only during the final Career OS Step 4 pull request workflow.

The final preservation script stopped because it assumed all required remote extensions must appear in the global WSL extension registry. The global registry contains `32` entries and did not list `davidanson.vscode-markdownlint`, even though markdownlint diagnostics worked in the live WSL workspace. This proves the assertion was too narrow, not that markdownlint failed. A final Linux-only inventory must inspect all WSL extension registries and profile-scoped extension state before Step 4.5c is closed.

During the final inventory:

- keep Windows VS Code closed;
- keep Docker Desktop stopped;
- do not reopen the fixture in VS Code;
- do not run the WSL `code` command;
- do not install, enable, disable, or remove any extension;
- do not install packages or dependencies;
- do not add a remote, push, or create a commit;
- do not begin Step 4.6 until the inventory is reviewed.

## Remaining Step 4 execution model

To avoid prolonged setup work, the remaining Step 4 plan is consolidated into three execution units:

1. **Step 4.5c: active.** Final extension-scope inventory and acceptance of the consolidated editor workflow.
2. **Step 4.6:** consolidated Container Tools, Dev Container, Python runtime, notebook-when-justified, and container end-to-end validation.
3. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance review, pull request, merge, and branch cleanup. This absorbs the former Step 4.8 final checkpoint.

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

## Accepted WSL baseline before remote editor correction

```text
VS Code and WSL Server version: 1.129.1
Client and server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 4b9f353855851e1923fe468b7a9b68ae949ff508dc31d59d1b2ba48a48b055a6
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
```

The extension registry and extension-directory baselines may legitimately change after the authorised installation or activation of Python, Ruff, and markdownlint in `WSL: Ubuntu`. The final inventory will establish the accepted post-correction baseline.

## Step 4.5a result

```text
interop_classification=HEALTHY_AFTER_CONTROLLED_RESTART
step_4_5a_post_restart_interop=PASS
step_4_5a_closed_editor_preflight=PASS
```

Git `2.43.0`, the expected global identity, diagnostic Python, and standard-library unittest are available. Ruff, `markdownlint`, and `markdownlint-cli2` host CLIs are absent. No global host CLI installation is required.

## Step 4.5b fixture checkpoint

Disposable local fixture:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
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

## Step 4.5c evidence

### Live context

```text
step_4_5c_live_context=PASS
```

Verified exact fixture path, Bash integrated terminal, Ubuntu WSL context, branch `main`, accepted fixture commit, one commit, clean worktree, and zero remotes.

### Editor workflow recovery

The editor-generated diff was exactly:

```diff
-def add(left:int,right:int)->int:
-    return left+right
+def add(left: int, right: int) -> int:
+    return left + right
```

The dependency-free test passed before restoration. The fixture then returned to the accepted commit and clean state:

```text
git_head_check=PASS
git_commit_count_check=PASS
git_clean_worktree_check=PASS
git_remote_count_check=PASS
tracked_file_count_check=PASS
step_4_5c_editor_recovery=PASS
```

### Closed Windows state

```text
windows_code_process_count=0
windows_code_process_check=PASS
step_4_5c_windows_closed=PASS
```

### Final inventory correction

The Linux-only preservation check passed settings and server-shutdown assertions, then reported:

```text
remote_registry_count=32
required_remote_extension_missing=['davidanson.vscode-markdownlint']
remote_copilot_entries=[]
required_remote_extension_registry_check=FAIL
```

Because markdownlint diagnostics worked in the live WSL workspace, the missing global-registry entry must be investigated across profile-scoped registries and extension storage. No extension change is authorised during this inventory.

## Known host issue

WSL-to-Windows executable interoperability has disappeared more than once during Step 4. This is a known host defect for the current setup, not a blocker for editor or container work.

Operational rule:

- perform Windows process checks from Windows PowerShell;
- keep Ubuntu preservation checks Linux-only;
- do not add a persistent `binfmt_misc` service, manual handler, or configuration workaround during Step 4;
- record the defect during final Step 4 known-issue review.

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

No functional editor blocker remains.

Step 4.5c requires one final read-only extension-scope inventory to establish the accepted post-correction WSL extension baseline. Step 4.6 remains blocked until that inventory is reviewed.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private