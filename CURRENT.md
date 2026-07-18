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

The current subtask remains **Step 4.5a: closed-editor preflight for the disposable editor-workflow fixture**.

The Windows executable interoperability failure has been repaired through the approved controlled WSL restart. The remaining Step 4.5a checks are workspace state, Git identity, diagnostic Python, unittest, optional host CLI inventory, and full baseline preservation.

During the remaining preflight:

- keep Windows VS Code closed;
- keep Docker Desktop stopped;
- use the standalone Ubuntu terminal only;
- do not create or modify fixture files;
- do not run the WSL `code` command;
- do not install packages or Python dependencies;
- do not change extensions, settings, interpreters, tests, terminals, profiles, Settings Sync, or Copilot controls;
- do not open a Dev Container;
- do not begin Step 4.5b, Step 4.6, or Step 5.

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

The fixture may later become a small local Git repository containing only harmless smoke-test files. It will not be pushed, published, or treated as a portfolio project.

Ubuntu system Python may be used only for a dependency-free, standard-library smoke check. No project dependency may be installed into Ubuntu system Python. Substantial runtime validation remains reserved for the repository-owned Dev Container in Step 4.6.

## Step 4.5 staged sequence

1. **Step 4.5a: active.** Closed-editor preflight. Interoperability recovery passed; remaining tool and baseline checks pending.
2. **Step 4.5b:** create the disposable local Git fixture with minimal Python, unittest, Markdown, project Ruff configuration, and repository-local VS Code test settings.
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

## Step 4.5a interoperability evidence

### Failure classification

The first preflight stopped when Ubuntu attempted to execute Windows PowerShell:

```text
cannot execute binary file: Exec format error
```

A separate Windows diagnostic proved Windows VS Code was closed. The Ubuntu diagnostic then proved:

```text
binfmt_misc_status=enabled
wslinterop_registration=ABSENT
cmd_probe_exit_code=126
windows_executable_probe_check=FAIL
interop_classification=NOT_HEALTHY
```

No fixture or configuration state changed.

### Controlled restart result

Docker Desktop was stopped before recovery. The Windows restart block passed:

```text
windows_code_process_check=PASS
running_distribution_count_before=0
running_distribution_safety_check=PASS
wsl_shutdown_exit_code=0
wsl_shutdown_command_check=PASS
running_distribution_count_after=0
wsl_stopped_state_check=PASS
process_termination_performed=WSL_SHUTDOWN_ONLY
configuration_change_performed=NO
step_4_5a_controlled_wsl_shutdown=PASS
```

### Post-restart interoperability result

After Ubuntu restarted normally:

```text
WSL_INTEROP=/run/WSL/314_interop
init_process=systemd
vscode_server_process_count=0
binfmt_misc_status=enabled
interop_handler_count=1
interop_handler=WSLInterop
cmd_probe_exit_code=0
powershell_probe_exit_code=0
cmd_interop_probe_check=PASS
powershell_interop_probe_check=PASS
interop_classification=HEALTHY_AFTER_CONTROLLED_RESTART
step_4_5a_post_restart_interop=PASS
```

The accepted Windows settings, WSL settings, extension registry, extension directories, remote profile storage, and empty workspace hashes all remained unchanged.

The `cmd.exe` probe printed the expected harmless UNC working-directory warning and then returned the required marker. PowerShell executed successfully without warning.

No manual handler registration, configuration edit, package installation, extension change, directory deletion, VS Code launch, Docker Desktop restart, or WSL `code` invocation occurred.

## Definition of done for Step 4.5a

Step 4.5a is complete only when read-only evidence proves:

- Windows VS Code remains closed;
- the Ubuntu VS Code Server process count is zero;
- Windows executable interoperability is healthy;
- the temporary workspace exists, remains empty, and is not already a Git repository;
- the workspace remains owned by `akcoo:akcoo`, mode `755`, on `ext4`;
- Git and the expected global identity are available;
- `/bin/python3` and the standard-library unittest runner are available;
- no active virtual environment, Conda environment, or `PYTHONPATH` exists;
- Ruff and markdownlint command-line availability is inventoried without installing anything;
- accepted Windows and WSL settings and storage baselines remain preserved;
- the WSL `code` command is not invoked.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Do not manually register `binfmt_misc` handlers or add a persistent repair service.
- Do not edit `/etc/wsl.conf` or `.wslconfig` without evidence that the normal restart path no longer works.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not install packages or project dependencies into Ubuntu system Python.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve the Step 3 host, WSL, Docker, and Windows interoperability architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

The interoperability blocker is resolved.

Step 4.5a remains incomplete only because its remaining read-only workspace, Git, Python, unittest, optional CLI, and preservation checks have not yet run after recovery.

## Next action

Keep Docker Desktop and VS Code closed. Run the revised Step 4.5a read-only preflight from the standalone Ubuntu terminal. Return the complete output. Stop before creating the fixture or opening VS Code.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.