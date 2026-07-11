# WSL Environment Standard

## Purpose

This document defines the minimum personal development environment for Career OS on Windows using WSL and Docker.

## Architectural decision

Use Windows as the host operating system, Visual Studio Code as the editor, WSL 2 with Ubuntu as the primary source workspace, and Docker Desktop with its WSL 2 backend as the default project runtime and dependency-isolation layer.

Project repositories developed with Linux tools must live in the Linux filesystem, normally under:

```text
~/projects
```

Do not place active Linux-developed repositories under Windows-mounted paths such as `/mnt/c/Users/...` unless a specific interoperability need justifies the trade-off.

Python versions, system packages, and Python dependencies for substantial Python projects must be defined in project-owned container configuration, normally a `Dockerfile` plus pinned dependency metadata. Docker Compose is added only when multiple services or durable supporting services justify it.

Do not install project packages globally into Ubuntu's system Python. Direct project `venv`, Conda, and Miniforge environments are not the default Career OS workflow.

## Step 3 completion condition

Step 3 is complete only when all of the following are verified:

- WSL 2 is installed and healthy;
- one Ubuntu distribution is available and set as the default;
- a non-root Linux user is configured;
- `~/projects` exists in the Linux filesystem;
- Git is installed and has the intended identity and authentication configuration;
- essential shell tools are available;
- Docker Desktop uses the WSL 2 backend;
- Docker Desktop integration is enabled for Ubuntu;
- Docker commands from Ubuntu reach the Docker Desktop engine;
- a small Python image can be built and run from a project under `~/projects` without installing project dependencies globally;
- Windows VS Code can open the Linux-filesystem project through WSL;
- the same project can be opened or run through a Dev Container when the project workflow justifies it.

## Gated execution sequence

### Step 3.1 — Inventory

Collect Windows, WSL, distribution, virtualization, Git, Python, Docker, and VS Code facts without changing the machine.

### Step 3.2 — WSL platform

Install, update, or repair WSL only as required by the inventory. Prefer WSL 2 and one supported Ubuntu distribution. Avoid multiple distributions until a real need exists.

### Step 3.3 — Linux identity and base tools

Verify the non-root Linux user, package health, and the minimum host toolchain. The host Python installation is available for operating-system needs but is not the default project dependency environment.

### Step 3.4 — Project filesystem

Create `~/projects` and verify that active Linux-developed repositories are stored there rather than under `/mnt/c`.

### Step 3.5 — Git

Configure Git inside WSL. Windows Git and WSL Git are separate installations and configurations.

### Step 3.6 — Containerized Python runtime

Preserve source under `~/projects`. Verify Docker Desktop's WSL 2 engine and Ubuntu integration, then build and run a minimal Python project from a repository-owned `Dockerfile`. Do not install project packages globally into Ubuntu. Do not install a second Docker Engine inside Ubuntu when Docker Desktop integration is the selected architecture.

### Step 3.7 — VS Code connectivity

Verify that the Windows VS Code client can open a folder through WSL and that the integrated terminal and file paths belong to Linux. Verify Dev Containers connectivity only after the Docker runtime check passes.

### Step 3.8 — End-to-end test

Create a harmless test project under `~/projects`, run its Python code through Docker from Ubuntu, open it through VS Code connected to WSL, and reopen it in a Dev Container when appropriate. Record the verified environment state and remove only explicitly disposable test artifacts.

## Container rules

- Prefer official, minimal base images pinned to a deliberate version.
- Keep dependency declarations and run instructions in the repository.
- Use `.dockerignore` to exclude Git metadata, caches, secrets, datasets, and unnecessary build context.
- Do not bake credentials, private datasets, WQU materials, or employer information into images.
- Use bind mounts for source during development only when the workflow needs live editing.
- Use named volumes for durable container-managed data where justified.
- Run application processes as a non-root user when practical.
- Add Compose only for real multi-service needs.
- Treat GPU support, ports, secrets, file ownership, image cleanup, and storage use as explicit project decisions.
- Do not containerize trivial documentation work merely for consistency or appearance.

## Minimum-change rule

Do not reinstall, unregister, convert, or delete a Linux distribution merely to obtain a clean setup. First inspect the existing state and preserve useful configuration. `wsl --unregister` is destructive and is not part of the normal setup path.

Use Docker Desktop's existing WSL 2 backend rather than installing a competing Docker Engine directly inside Ubuntu, unless a future documented decision changes the architecture.

## Scope boundary

Step 3 covers the operating environment, Docker runtime verification, and a basic VS Code/Dev Containers connection test. Broader extension profiles, Jupyter customization, production orchestration, registry workflows, CI/CD, and automatic AI-completion controls belong to later steps or to a real project that requires them.