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

**Step 4.6 is complete.**

The next gated unit is **Step 4.7: consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance, pull request, merge, and branch cleanup**.

Step 4.7 has not started and requires Ayush to say:

```text
Proceed to Step 4.7
```

Until then:

- keep VS Code closed;
- leave Docker Desktop running;
- do not reopen or rebuild the Dev Container;
- do not edit the disposable fixture;
- do not edit either Windows profile settings file;
- do not prune Docker or delete images, containers, or volumes;
- do not install packages or dependencies;
- do not add a remote, push, or create another fixture commit;
- do not begin Step 5.

## Remaining Step 4 execution model

1. **Step 4.6: complete.** Consolidated Container Tools, Dev Container, Python runtime, justified notebook, editor, test, Markdown, restoration, and preservation validation.
2. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance, pull request, merge, and branch cleanup.

Step 4.7 remains gated.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: complete.** Consolidated container workflow and preservation.
7. **Step 4.7:** consolidated AI boundary and final Step 4 closure.

## Accepted Windows VS Code baseline after Step 4.6

- Profile: `Career OS Engineering`
- Persistent profile directory ID: `-639a60a5`
- Career OS local extension membership: exactly `15`
- Default extension membership: `36`
- No Windows Python interpreter in the Career OS profile
- No global test framework, terminal profile, Ruff rule configuration, or keybindings
- Automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions disabled
- `chat.disableAIFeatures` unset
- Settings Sync unchanged
- `terminal.integrated.initialHint` is `false`

The added terminal setting suppresses only the integrated terminal's introductory hint. It does not select or change a shell, terminal profile, environment, interpreter, test framework, Settings Sync, or automatic-AI behaviour. It is accepted as a benign VS Code-managed profile preference and does not require correction.

```text
Default settings hash: e5ffc83c78e5ade86a903ef0a45b660b2c65af6eb6c300e8aa92d86cda110389
Career OS settings hash before Step 4.6: fd57d528636ff3bc99cec37251406745392f7af6fba68c8e1b39ddc7c0527ada
Accepted Career OS settings hash after Step 4.6: 6218b6bfbdbef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
```

## Settings diagnostic acceptance

The read-only Windows PowerShell diagnostic passed:

```text
windows_code_process_check=PASS
career_settings_presence_check=PASS
career_settings_json_parse_check=PASS
approved_core_settings_check=PASS
career_settings_read_only_check=PASS
configuration_change_performed=NO
step_4_6_career_settings_diagnostic=COMPLETE
```

The exact semantic difference was:

```text
semantic_diff=ADDED|terminal.integrated.initialHint|actual=false
semantic_difference_count=1
expected_core_failure_count=0
```

The five automatic-AI controls, minimum editor and Git settings, and all other approved core settings remained unchanged. No Windows Python interpreter, project test setting, shell selection, terminal profile, Settings Sync setting, or `chat.disableAIFeatures` setting was added.

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

## Step 4.6 completion evidence

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

### Restoration, Docker lifecycle, and preservation

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

The Dev Container lifecycle was accepted as `STOPPED_PRESENT`. The generated image remains available under its VS Code-generated tag. Retention of the original source-image tag is not required after a successful build and live-runtime validation.

No Docker prune, image deletion, volume deletion, host package installation, remote, push, extra fixture commit, or public action occurred.

## Step 4.6 completion decision

Step 4.6 is complete because the repository-owned Dev Container workflow successfully proved:

- Docker Desktop and Ubuntu WSL engine access;
- repository-owned runtime definition;
- isolated container Python and pinned notebook kernel;
- Python execution and unittest;
- Ruff, markdownlint, Markdown preview, Test Explorer, and notebook execution inside the container;
- container lifecycle and Docker resource visibility;
- exact fixture restoration and clean Git state;
- preservation of all material Windows and WSL settings and extension boundaries.

The accepted `terminal.integrated.initialHint=false` addition is cosmetic and does not weaken any Career OS architecture or safety boundary.

## Known issues for Step 4.7 review

### WSL interoperability

WSL-to-Windows executable interoperability disappeared more than once during Step 4.

Operational rule:

- perform Windows process checks from Windows PowerShell;
- keep Ubuntu preservation checks Linux-only;
- do not add a persistent `binfmt_misc` service, manual handler, or WSL configuration workaround during Step 4;
- review and record the defect during Step 4.7 acceptance.

### Ruff formatting discrepancy

The container formatter reformatted the function signature but did not add spaces around `+` in the intentionally compressed return expression during the observed save. Ruff activation and format-on-save were proven. Treat this as minor non-blocking evidence to review during Step 4.7, not as a reason to extend environment setup.

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

No technical blocker is known.

Step 4.7 remains blocked only by the explicit approval gate.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
