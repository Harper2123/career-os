# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` represents the last merged top-level checkpoint.
- All Step 4 work remains on this branch.
- One pull request will be created only after full Step 4 acceptance.
- Unrelated work must not be added to this branch.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The environment must support Python, justified notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.6 is active and in final focused closure.**

The consolidated container workflow has passed its fixture, engine, runtime, editor, test, Markdown, notebook-kernel, saved notebook-output, and Windows close checks. One revised Linux-only restoration and preservation block remains.

Do not reopen VS Code or rebuild the Dev Container.

During final closure:

- keep VS Code closed;
- keep Docker Desktop running;
- use the standalone Ubuntu terminal only;
- record the current Docker container and image inventory without requiring the source image tag to remain;
- restore the two temporary tracked-file changes to the accepted fixture commit;
- preserve all Windows and WSL profile settings;
- do not prune Docker, delete images or volumes, install packages, add a remote, push, or create another commit;
- do not begin Step 4.7 or Step 5 until the closure evidence is reviewed.

## Remaining Step 4 execution model

1. **Step 4.6: active.** Final restoration and preservation closure for the consolidated container workflow.
2. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance, pull request, merge, and branch cleanup.

Step 4.7 remains gated.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: active.** Consolidated container workflow and final focused closure.
7. **Step 4.7:** consolidated AI boundary and final Step 4 closure.

## Accepted Windows VS Code baseline

- Profile: `Career OS Engineering`
- Persistent profile directory ID: `-639a60a5`
- Career OS local extension membership: exactly `15`
- Default extension membership: `36`
- No Windows Python interpreter in the Career OS profile
- No global test framework, terminal profile, Ruff rule configuration, or keybindings
- Automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions disabled
- `chat.disableAIFeatures` unset
- Settings Sync unchanged

```text
Default settings hash: e5ffc83c78e5ade86a903ef0a45b660b2c65af6eb6c300e8aa92d86cda110389
Career OS settings hash: fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada
```

## Accepted WSL baseline after Step 4.5

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

## Step 4.6 repository-owned fixture

Approved additions:

```text
.devcontainer/devcontainer.json
requirements-dev.txt
notebooks/container_smoke.ipynb
.gitignore update for .ipynb_checkpoints/
```

Accepted committed state:

```text
Path: /home/akcoo/projects/career-os-vscode-wsl-check
Branch: main
Head: fe5e9f30ce7301f833818fd4c24b33e19695846a
Latest subject: test: add disposable dev container workflow
Commit count: 2
Tracked files: 12
Git remotes: 0
Expected clean tree hash: 806cfdb2cc35b2f86327a6e6a7a1068ffdd11ae0bf0fa4189677fa2649f982c5
```

The fixture is local-only and must not be pushed or treated as portfolio work.

## Step 4.6 evidence

### Fixture and Docker engine

```text
step_4_6_fixture_preparation=PASS
```

Verified:

- Docker context `default`;
- Docker client and server `29.4.3`;
- Linux `amd64` Docker Desktop engine;
- Compose `5.1.3`;
- repository source image `mcr.microsoft.com/devcontainers/python:1-3.12-bookworm`;
- pinned `ipykernel==7.3.0` declared only in the repository-owned container environment;
- no host virtual environment, Conda environment, host ipykernel, remote, push, daemon configuration change, or Docker deletion;
- fixture commit `fe5e9f30ce7301f833818fd4c24b33e19695846a` created with the approved files and exact expected hashes.

### Live Dev Container runtime

```text
step_4_6_container_runtime=PASS
```

Verified:

- container user `vscode`, UID `1000`;
- workspace `/workspaces/career-os-vscode-wsl-check`;
- Bash terminal;
- Debian `12`, x86_64;
- container Python `/usr/local/bin/python`, version `3.12.11`, prefix `/usr/local`;
- pinned ipykernel `7.3.0`;
- no virtual environment or Conda environment;
- branch `main`, two commits, twelve tracked files, clean worktree, zero remotes before editor changes;
- package execution returned `42`;
- unittest passed;
- live devcontainer name and image checks passed.

Observed running container name:

```text
vsc-career-os-vscode-wsl-check-f4856169806bc0c1c53fc5c02ee74bc09ac1b452c5c2d92328d5f79172b04396-uid
```

### Live editor workflow

Ayush confirmed:

- Ruff reported the intentional unused-import diagnostic;
- Ruff format-on-save changed the Python file;
- markdownlint reported the intentional heading-level diagnostic;
- Markdown preview worked;
- the Testing beaker appeared and the unittest passed;
- the notebook kernel was selected from `/usr/local/bin/python` inside the container;
- Source Control showed exactly the Python and notebook changes.

Saved Python result:

```text
ruff_saved_result=FORMATTER_INVOKED_PARTIAL_RESULT
ruff_format_invocation_evidence=PASS
```

The formatter changed the function signature spacing but left `return left+right` unchanged. This is a recorded minor non-blocking discrepancy because formatter activation and Ruff diagnostics are both proven.

### Saved notebook evidence

The focused closure proved:

```text
expected_temporary_change_set_check=PASS
notebook_execution_count=1
notebook_execution_count_check=PASS
notebook_container_python_check=PASS
notebook_saved_output_check=PASS
```

Saved output:

```text
python_executable=/usr/local/bin/python
python_version=3.12.11
container_notebook_smoke=PASS
```

### Close and Docker lifecycle

Windows VS Code closed normally:

```text
windows_code_process_check=PASS
step_4_6_windows_closed=PASS
```

A Docker query after close found zero matching containers. The exact source image tag also was no longer present:

```text
Error response from daemon: No such image: mcr.microsoft.com/devcontainers/python:1-3.12-bookworm
```

The source-tag assertion was too strict. The successful live container runtime already proves that the repository-owned definition built and ran from the approved source image. Step 4.6 acceptance does not require Docker Desktop to retain that exact source tag or the generated container after VS Code closes. The final closure records the current non-destructive image inventory instead of requiring a particular retained tag.

No Docker prune, image deletion, or volume deletion was performed by Ayush.

## Final focused closure definition of done

Step 4.6 closes when one Linux-only block proves:

- Docker Desktop remains reachable through the Linux engine;
- no matching Dev Container is running;
- current matching-container and image inventory is recorded without requiring a specific retained tag;
- the two expected temporary changes are restored to `HEAD`;
- the fixture returns to branch `main`, head `fe5e9f30ce7301f833818fd4c24b33e19695846a`, two commits, twelve tracked files, zero remotes, clean worktree, and expected tree hash;
- host unittest passes;
- protected Windows and WSL settings and extension baselines remain unchanged;
- no prune, image or volume deletion, package installation, remote, push, extra commit, or public action occurs.

## Known host issue

WSL-to-Windows executable interoperability has disappeared more than once during Step 4.

Operational rule:

- perform Windows process checks from Windows PowerShell;
- keep Ubuntu preservation checks Linux-only;
- do not add a persistent `binfmt_misc` service, manual handler, or WSL configuration workaround during Step 4;
- record and review the defect during Step 4.7 acceptance.

## MScFE state

- Completed courses: Financial Markets, Financial Data, Financial Econometrics
- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, course work, and recovery take priority over optional setup or personal engineering work
- Once the course begins, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week
- No guilt debt applies to unfinished setup work

## Governing constraints

- Prefer the minimum reliable configuration over completeness for its own sake.
- Finish and record minor technical debt rather than extending setup indefinitely.
- Preserve the Default profile and existing tools.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not install project dependencies into Ubuntu system Python.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No functional container blocker remains. Step 4.6 requires only the revised Linux-only restoration and preservation block.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
