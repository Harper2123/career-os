# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is active.

## Active setup branch

- Working branch: `setup/step-4`
- `main` is the last merged top-level checkpoint.
- All Step 4 work remains on `setup/step-4`.
- One pull request will be created only after full Step 4 acceptance.
- Unrelated work must not be added to this branch.

## Current objective

Configure Windows Visual Studio Code as the minimum reliable engineering control centre for work performed through Ubuntu WSL and repository-owned containers.

The environment must support Python, justified notebooks, Markdown, tests, Git operations, terminal commands, Docker, WSL, and Dev Containers without excessive customisation or automatic AI completion.

## Current task

**Step 4.6 is active and at its final preservation diagnostic.**

The consolidated container workflow has passed its fixture, Docker engine, Dev Container runtime, container Python, pinned notebook kernel, editor, test, Markdown, notebook-output, restoration, Docker lifecycle, and Linux preservation checks.

The last continuation restored the fixture successfully and passed every protected baseline except the Windows `Career OS Engineering` profile settings hash:

```text
expected: fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada
actual:   6218b6bfbdbef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
```

All other settings and extension baselines remained unchanged. Step 4.6 therefore requires one read-only Windows PowerShell diagnostic to identify the exact settings drift before any correction or acceptance decision.

Until that diagnostic is reviewed:

- keep VS Code closed;
- keep Docker Desktop running;
- do not reopen or rebuild the Dev Container;
- do not edit either Windows profile settings file;
- do not edit the fixture;
- do not prune Docker or delete images, containers, or volumes;
- do not install packages or dependencies;
- do not add a remote, push, or create another fixture commit;
- do not begin Step 4.7 or Step 5.

## Remaining Step 4 execution model

1. **Step 4.6: active.** Diagnose and resolve or accept the single Career-profile settings drift, then close the consolidated container workflow.
2. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance, pull request, merge, and branch cleanup.

Step 4.7 remains gated.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: active.** Consolidated container workflow, final settings-drift diagnostic pending.
7. **Step 4.7:** consolidated AI boundary and final Step 4 closure.

## Accepted Windows VS Code baseline before Step 4.6

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
Career OS settings hash before Step 4.6: fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada
Career OS settings hash after Step 4.6: 6218b6bfbdbef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
```

## Accepted WSL baseline

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

These WSL baselines all passed after the container session.

## Step 4.6 fixture checkpoint

```text
Path: /home/akcoo/projects/career-os-vscode-wsl-check
Branch: main
Head: fe5e9f30ce7301f833818fd4c24b33e19695846a
Latest subject: test: add disposable dev container workflow
Commit count: 2
Tracked files: 12
Git remotes: 0
Worktree: clean
Tree hash: 806cfdb2cc35b2f86327a6e6a7a1068ffdd11ae0bf0fa4189677fa2649f982c5
```

The fixture is local-only and must not be pushed or treated as portfolio work.

## Step 4.6 accepted evidence

### Fixture and engine

```text
step_4_6_fixture_preparation=PASS
```

Verified Docker Desktop WSL2 engine, Docker and Compose commands, repository-owned configuration, exact fixture hashes, pinned `ipykernel==7.3.0`, no host project dependency, and one approved local fixture commit.

### Live Dev Container runtime

```text
step_4_6_container_runtime=PASS
```

Verified:

- container user `vscode`, UID `1000`;
- workspace `/workspaces/career-os-vscode-wsl-check`;
- Debian 12, x86_64;
- Python `/usr/local/bin/python`, version `3.12.11`;
- `ipykernel==7.3.0`;
- package execution returned `42`;
- unittest passed;
- branch `main`, two commits, twelve tracked files, zero remotes;
- Dev Container name and image configuration passed.

Observed lifecycle resources:

```text
Container name while live: vsc-career-os-vscode-wsl-check-f4856169806bc0c1c53fc5c02ee74bc09ac1b452c5c2d92328d5f79172b04396-uid
Container ID after close: cc661a3a5f49
Container display name after close: eager_euclid
Container state after close: exited
Generated image ID: sha256:4025f17533ee4a3b2ac50ca6d42af180a4fa98463c14f3fea24f3e239739e49c
Generated image size: 2.24GB
```

### Editor and notebook workflow

Verified:

- Ruff reported the intentional unused import;
- Ruff format-on-save was invoked and reformatted the function signature;
- the remaining `return left+right` spacing is recorded as a minor non-blocking formatter discrepancy;
- markdownlint reported the intentional heading issue;
- Markdown preview worked;
- Test Explorer discovered and passed the unittest;
- the notebook selected `/usr/local/bin/python`;
- notebook output contained Python `3.12.11` and `container_notebook_smoke=PASS`;
- Source Control showed exactly the Python and notebook changes.

### Final continuation

Passed:

```text
expected_temporary_change_set_check=PASS
saved_notebook_evidence_from_prior_run=PASS
docker_linux_engine_check=PASS
running_fixture_container_count_check=PASS
matching_container_stopped_state_check=PASS
container_lifecycle_acceptance=PASS
docker_image_inventory_recorded=PASS
temporary_editor_output_restored=PASS
fixture_branch_check=PASS
fixture_head_check=PASS
fixture_commit_count_check=PASS
fixture_clean_worktree_check=PASS
fixture_remote_count_check=PASS
fixture_tracked_file_count_check=PASS
fixture_tree_hash_check=PASS
closed_host_unittest_execution=PASS
vscode_server_process_count_check=PASS
machine_settings_hash_check=PASS
global_registry_hash_check=PASS
extension_directory_names_hash_check=PASS
remote_profile_directory_names_hash_check=PASS
all_extension_registries_hash_check=PASS
default_settings_hash_check=PASS
```

Failed only:

```text
career_settings_hash_check=FAIL
```

## Definition of done for the settings diagnostic

The diagnostic is complete when read-only evidence shows:

- the current UTF-8 contents of the Career profile settings file;
- the exact top-level setting keys and values;
- the file size and last-write timestamp;
- whether the five automatic-AI controls remain enforced;
- whether the minimum editor and Git settings remain enforced;
- whether any interpreter, test framework, terminal, Settings Sync, or unrelated setting was added;
- the exact semantic difference from the approved baseline;
- no file modification occurs during the diagnostic.

After review, the drift will be either accepted as a justified VS Code-managed addition or corrected through one explicit, reversible settings update.

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

One read-only Windows PowerShell diagnostic of the changed Career profile settings file.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
