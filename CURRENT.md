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

The current subtask is **Step 4.5a: run a closed-editor preflight for the disposable editor-workflow fixture**.

During Step 4.5a:

- keep Windows VS Code closed;
- use the standalone Ubuntu terminal only;
- inspect the temporary workspace and tool availability without creating or modifying files;
- do not run the WSL `code` command;
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

Step 4.5 will use the disposable workspace:

```text
/home/akcoo/projects/career-os-vscode-wsl-check
```

The fixture may later become a small local Git repository containing only harmless smoke-test files. It will not be pushed, published, or treated as a portfolio project.

Ubuntu system Python may be used only for a dependency-free, standard-library smoke check. No project dependency may be installed into Ubuntu system Python. Substantial runtime validation remains reserved for the repository-owned Dev Container in Step 4.6.

## Step 4.5 staged sequence

1. **Step 4.5a: active.** Closed-editor preflight for workspace state, Git, diagnostic Python, test runner availability, environment isolation, and preserved VS Code baselines.
2. **Step 4.5b:** create the disposable local Git fixture with minimal Python, unittest, Markdown, project Ruff configuration, and repository-local VS Code test settings.
3. **Step 4.5c:** open the fixture through Windows VS Code using `Career OS Engineering` and Ubuntu WSL, then verify profile continuity and terminal context.
4. **Step 4.5d:** validate Python editing, language support, Ruff diagnostics, and format-on-save.
5. **Step 4.5e:** validate Markdown editing, built-in preview, and markdownlint diagnostics.
6. **Step 4.5f:** validate unittest discovery and execution through VS Code using only the dependency-free host smoke fixture.
7. **Step 4.5g:** validate built-in Source Control inspection and GitHub Pull Requests access without pushing, creating a pull request, or changing the public repository.
8. **Step 4.5h:** run the final editor-workflow preservation checkpoint and leave cleanup for the explicitly authorised later step.

Each substep begins only after the previous substep's evidence is reviewed.

## Step 4.3 Windows profile checkpoint

The verified Windows profile state remains:

- profile name: `Career OS Engineering`;
- created from Empty Profile;
- persistent profile directory ID: `-639a60a5`;
- Career OS extension membership: exactly `15` approved entries;
- Default extension membership: `36`;
- no Windows Python interpreter configured in the Career OS profile;
- no global test framework, terminal profile, Ruff rule configuration, or keybindings;
- automatic inline suggestions, Copilot completion, next-edit suggestions, automatic rename suggestions, and AI code actions disabled across Default and Career OS profiles;
- `chat.disableAIFeatures` unset so deliberate manual chat remains available;
- Settings Sync unchanged.

Verified Windows settings hashes:

```text
Default: E5FFC83C78E5ADE86A903EF0A45B660B2C65AF6EB6C300E8AA92D86CDA110389
Career OS Engineering: FD57D528636FF3BC99CEC37251406745392F7AF6FBA68C8E1B39DDC7C0527ADA
```

## Step 4.4 WSL checkpoint

Overall result:

```text
step_4_4_wsl_profile_validation=PASS
```

Accepted current client and WSL Server state:

```text
VS Code version: 1.129.1
Client and WSL Server commit: 8a7abeba6e03ea3af87bfbce9a1b7e48fed567b8
```

Accepted current WSL baselines:

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
- integrated terminal uses Bash and starts in the workspace;
- no active virtual environment, Conda environment, or `PYTHONPATH`;
- `/bin/python3` resolves to Ubuntu diagnostic Python `3.12.3`;
- WSL machine setting remains `python.defaultInterpreterPath="/bin/python3"`;
- WSL user-extension registry contains `32` entries and no Copilot package;
- twenty excluded extension packages remain stored but inactive;
- no manual extension-directory deletion is authorised.

## Definition of done for Step 4.5a

Step 4.5a is complete only when read-only evidence proves:

- Windows VS Code remains closed;
- the Ubuntu VS Code Server process count is zero;
- the temporary workspace exists, remains empty, and is not already a Git repository;
- the workspace remains owned by `akcoo:akcoo`, mode `755`, on `ext4`;
- Git is available and the expected global identity remains configured;
- `/bin/python3` is available as diagnostic Python;
- the standard-library unittest runner is available;
- no active virtual environment, Conda environment, or `PYTHONPATH` exists;
- Ruff and markdownlint command-line availability is inventoried without installing anything;
- the accepted WSL settings, registry, extension-directory, remote-profile, and workspace hashes remain unchanged;
- the WSL `code` command is not invoked.

## Governing constraints

- Prefer the minimum useful configuration.
- Preserve the Default profile and its installed tools.
- Prefer profile isolation over uninstalling extensions.
- Do not manually delete extension, profile, VS Code Server, or versioned VS Code installation directories.
- Do not add extensions merely because they are popular.
- Do not configure a global Python test framework.
- Ubuntu system Python may be used only for operating-system diagnostics and lightweight dependency-free host checks.
- Do not install project dependencies into Ubuntu system Python.
- Substantial Python projects use repository-owned Dev Containers.
- Keep automatic AI completion disabled by default.
- Preserve manual AI chat only as a deliberately invoked tool after a first attempt.
- Preserve the Step 3 host, WSL, and Docker architecture.
- Do not begin Step 5 during Step 4.
- Do not commit credentials, private course material, private datasets, employer information, or personal health information.

## Immediate blocker

No technical blocker is known. Step 4.5a requires the approved read-only preflight from the standalone Ubuntu terminal.

## Next action

Run the Step 4.5a preflight from the active setup conversation and return the complete output. Then stop before creating the fixture or reopening VS Code.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- Completed MScFE courses: Financial Markets, Financial Data, Financial Econometrics
- Anticipated next course: Derivative Pricing, subject to enrollment confirmation
- No active flagship project
- Raw WQU materials remain private
- During an active MScFE course, unrelated personal AI engineering remains capped at approximately 3 to 4 hours per week.
