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

**Step 4.5a is complete.** The current subtask is **Step 4.5b: create and verify the disposable local editor-workflow fixture**.

During Step 4.5b:

- keep Windows VS Code closed;
- keep Docker Desktop stopped;
- use the standalone Ubuntu terminal only;
- create files only inside `/home/akcoo/projects/career-os-vscode-wsl-check`;
- initialise only that folder as a local Git repository;
- create no remote and perform no push;
- use Ubuntu system Python only for the dependency-free fixture and verification;
- do not install packages or Python dependencies;
- do not run the WSL `code` command;
- do not change user, profile, machine, extension, interpreter, terminal, Settings Sync, or Copilot settings;
- do not open a Dev Container;
- do not begin Step 4.5c, Step 4.6, or Step 5 until the fixture evidence is reviewed.

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

The fixture will be a small local Git repository containing only harmless smoke-test files. It will not be pushed, published, connected to a remote, or treated as a portfolio project.

Ubuntu system Python may be used only for a dependency-free, standard-library smoke check. No project dependency may be installed into Ubuntu system Python. Substantial runtime validation remains reserved for the repository-owned Dev Container in Step 4.6.

## Step 4.5 staged sequence

1. **Step 4.5a: complete.** Closed-editor preflight and controlled interoperability recovery.
2. **Step 4.5b: active.** Create and verify the disposable local Git fixture with minimal Python, unittest, Markdown, project Ruff configuration, and repository-local VS Code test settings.
3. **Step 4.5c:** open the fixture through Windows VS Code using `Career OS Engineering` and Ubuntu WSL, then verify profile continuity and terminal context.
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
Empty workspace hash: e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
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

### Interoperability recovery

The original preflight detected a missing WSL interoperability handler. A controlled recovery stopped Docker Desktop, confirmed VS Code and the VS Code Server were stopped, ran `wsl --shutdown`, and relaunched Ubuntu normally.

Post-restart evidence passed:

```text
interop_handler=WSLInterop
cmd_interop_probe_check=PASS
powershell_interop_probe_check=PASS
interop_classification=HEALTHY_AFTER_CONTROLLED_RESTART
step_4_5a_post_restart_interop=PASS
```

No persistent handler registration, WSL configuration edit, package installation, extension change, or directory deletion was performed.

### Revised closed-editor preflight

The complete preflight passed:

```text
windows_code_process_count_check=PASS
vscode_server_process_count_check=PASS
windows_executable_interop_reuse_check=PASS
workspace_empty_state_check=PASS
workspace_not_git_repository_check=PASS
git_command_presence_check=PASS
git_global_user_name_check=PASS
git_global_user_email_check=PASS
virtual_environment_absent_check=PASS
conda_environment_absent_check=PASS
pythonpath_absent_check=PASS
workspace_environment_absent_check=PASS
system_python_not_virtual_environment=PASS
unittest_import_check=PASS
unittest_runner_check=PASS
optional_cli_inventory=PASS
extension_registry_count_check=PASS
extension_registry_copilot_check=PASS
extension_registry_parse_check=PASS
workspace_stability_check=PASS
step_4_5a_closed_editor_preflight=PASS
```

Verified tool and environment state:

- Git `2.43.0` at `/usr/bin/git`;
- global Git identity `Ayush Kumar <akcoolkmr@gmail.com>`;
- Ubuntu Python `3.12.3` at `/bin/python3`, prefix and base prefix `/usr`;
- standard-library `unittest` import and runner available;
- Ruff CLI absent;
- `markdownlint` and `markdownlint-cli2` CLIs absent;
- no package installation performed.

The CLI absences are accepted inventory results. Step 4.5 will validate the installed VS Code extensions rather than installing global host tools.

All accepted Windows settings, WSL settings, extension registry, extension directories, remote profile storage, keybinding absence, and empty workspace baselines remained unchanged during the preflight.

## Definition of done for Step 4.5b

Step 4.5b is complete only when evidence proves:

- the previously empty workspace contains exactly the approved harmless fixture files and directories;
- the fixture is a local Git repository on branch `main` with one clean initial commit;
- no Git remote exists;
- Git author identity matches the approved global identity;
- the fixture contains no credential, private course, employer, client, dataset, or personal information;
- Python code and tests use only the standard library;
- `/bin/python3 -m unittest` passes without installing dependencies;
- repository-local VS Code settings enable unittest and disable pytest without setting a project interpreter;
- repository-local Ruff configuration exists in `pyproject.toml`;
- repository-local markdownlint configuration exists;
- one intentional Ruff diagnostic and one intentional markdownlint diagnostic remain for later editor validation;
- the accepted profile, settings, extension storage, and WSL baselines remain unchanged;
- Docker Desktop and VS Code remain closed;
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

Step 4.5b requires creation and verification of the approved disposable local fixture. Step 4.5c remains blocked until that evidence is reviewed.

## Next action

Keep Docker Desktop and VS Code closed. Run the approved Step 4.5b fixture-creation block from the standalone Ubuntu terminal. Return the complete output. Stop before opening VS Code.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.