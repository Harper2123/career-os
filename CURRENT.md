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

**Step 4.6 is active.**

The current execution unit is **consolidated Container Tools, Dev Container, Python runtime, justified notebook, and container end-to-end validation**.

Ayush explicitly requested consolidation so environment setup does not crowd out MScFE work. Step 4.6 is therefore one coherent gated unit rather than a chain of small substeps.

During Step 4.6:

- use the existing disposable local fixture at `/home/akcoo/projects/career-os-vscode-wsl-check`;
- start Docker Desktop normally and use its WSL2 backend;
- add a repository-owned `.devcontainer/devcontainer.json`;
- use the official Python 3.12 Bookworm Dev Container image;
- install only pinned `ipykernel==7.3.0` inside the container environment for the justified notebook smoke test;
- declare only Python, Ruff, Jupyter, and markdownlint as project container extensions;
- keep the project free of Windows Python, host project dependencies, Conda, and a host virtual environment;
- create one local validation commit, but create no remote and perform no push;
- validate Container Explorer, Dev Container connection, container Python, Ruff, unittest, Markdown, and one notebook cell;
- restore temporary editor and notebook output changes before closing;
- stop the Dev Container normally and preserve its stopped resources for final Step 4 cleanup;
- do not prune Docker, delete images, remove volumes, or manually delete VS Code Server or extension directories;
- do not begin Step 4.7 or Step 5 until this evidence is reviewed.

## Remaining Step 4 execution model

1. **Step 4.6: active.** Consolidated container workflow and preservation.
2. **Step 4.7:** consolidated automatic-AI boundary verification, final cleanup, known-issue review, Step 4 acceptance review, pull request, merge, and branch cleanup. This absorbs the former Step 4.8 checkpoint.

Step 4.7 remains gated and is not authorised merely by being listed.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: active.** Consolidated container workflow.
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
- Twenty previously excluded extension packages may remain stored but inactive

## Disposable fixture baseline before Step 4.6

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

## Approved Step 4.6 fixture additions

Step 4.6 may add and commit exactly these changes inside the disposable fixture:

```text
.devcontainer/devcontainer.json
requirements-dev.txt
notebooks/container_smoke.ipynb
.gitignore update for .ipynb_checkpoints/
```

Expected file hashes after creation:

```text
.devcontainer/devcontainer.json: 8198564d87ec06d56cd56e2da291cb167dcd6e8d75ba36e4ed5aeb792650ac2c
requirements-dev.txt: 2f44625f42539b6af58b181867fa0833d7df083c05d48e830ef9b106e4772c3a
notebooks/container_smoke.ipynb: 28bb6c3cb345e817ae22a74416cd85c755561fa2e062c99a8535e26d8f87aab8
.gitignore: 60400cb0f97a2c63188dda0d33f068063778300d2aca358789d56cbeac25a415
```

Expected non-Git fixture tree hash after the approved additions:

```text
806cfdb2cc35b2f86327a6e6a7a1068ffdd11ae0bf0fa4189677fa2649f982c5
```

## Definition of done for Step 4.6

Step 4.6 is complete only when evidence proves:

- Docker Desktop starts normally with its WSL2 backend;
- Ubuntu can access the Docker engine through the expected context;
- Docker and Compose commands work without changing daemon configuration;
- the repository-owned `devcontainer.json` parses and contains only the approved image, lifecycle command, and extension declarations;
- the local fixture has exactly two commits, remains on `main`, has zero remotes, and is clean before opening the container;
- VS Code opens the fixture in `Career OS Engineering` through Ubuntu WSL and then reopens it in the named Dev Container;
- Container Explorer displays the running Dev Container and its image;
- the integrated terminal runs as the non-root `vscode` user inside the container workspace;
- the active Python executable comes from the container, not Windows or Ubuntu host Python;
- pinned `ipykernel==7.3.0` is installed inside the container environment;
- dependency-free unittest passes inside the container;
- Python navigation and Ruff diagnostics and format-on-save work inside the container;
- the justified notebook selects the container Python kernel and executes its smoke cell successfully;
- Markdown preview remains functional;
- temporary Python formatting and notebook output changes are restored;
- the fixture returns to the approved Step 4.6 commit, expected tree hash, clean worktree, two commits, twelve tracked files, and zero remotes;
- VS Code closes normally and the Dev Container stops normally;
- protected Windows and WSL profile settings remain unchanged;
- no Docker prune, image deletion, volume deletion, remote, push, extra commit, global package install, host project dependency, or public action occurs.

## Known host issue

WSL-to-Windows executable interoperability has disappeared more than once during Step 4. A controlled `wsl --shutdown` restored it temporarily, but the failure later recurred.

Operational rule:

- perform Windows process checks from Windows PowerShell;
- keep Ubuntu preservation checks Linux-only;
- do not add a persistent `binfmt_misc` service, manual handler, or WSL configuration workaround during Step 4;
- record and review the defect during final Step 4 acceptance.

This issue does not block Step 4.6 because no required container validation depends on launching a Windows executable from Ubuntu.

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

Step 4.6 is authorised and active. Step 4.7 remains blocked until the consolidated Step 4.6 evidence is reviewed.

## Other Career OS state

- Active ChatGPT Project: `Career OS`
- Active setup conversation: `00 - Career OS Architecture & Setup`
- No active flagship project
- Raw WQU materials remain private
