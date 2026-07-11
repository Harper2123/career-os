# WSL Environment Standard

## Purpose

This document defines the minimum personal development environment for Career OS on Windows using WSL.

## Architectural decision

Use Windows as the host operating system, Visual Studio Code as the editor, and WSL 2 with Ubuntu as the primary Linux development environment.

Project repositories developed with Linux tools must live in the Linux filesystem, normally under:

```text
~/projects
```

Do not place active Linux-developed repositories under Windows-mounted paths such as `/mnt/c/Users/...` unless a specific interoperability need justifies the trade-off.

## Step 3 completion condition

Step 3 is complete only when all of the following are verified:

- WSL 2 is installed and healthy;
- one Ubuntu distribution is available and set as the default;
- a non-root Linux user is configured;
- `~/projects` exists in the Linux filesystem;
- Git is installed and has the intended name and email configuration;
- Python 3, `venv`, and `pip` are available;
- a project-specific virtual environment can be created and activated;
- essential shell tools are available;
- Windows VS Code can open a Linux-filesystem project through WSL;
- a small Python test project runs from that WSL-connected VS Code window.

## Gated execution sequence

### Step 3.1 — Inventory

Collect Windows, WSL, distribution, virtualization, Git, Python, and VS Code facts without changing the machine.

### Step 3.2 — WSL platform

Install, update, or repair WSL only as required by the inventory. Prefer WSL 2 and one supported Ubuntu distribution. Avoid multiple distributions until a real need exists.

### Step 3.3 — Linux identity and base tools

Verify the non-root Linux user, update packages, and install the minimum base toolchain.

### Step 3.4 — Project filesystem

Create `~/projects` and verify that active Linux-developed repositories are stored there rather than under `/mnt/c`.

### Step 3.5 — Git

Configure Git inside WSL. Windows Git and WSL Git are separate installations and configurations.

### Step 3.6 — Python

Use the distribution's Python 3 for bootstrap work and project-local virtual environments created with `python3 -m venv .venv`. Do not install project packages globally with `sudo pip`.

### Step 3.7 — VS Code connectivity

Verify that the Windows VS Code client can open a folder through WSL and that the integrated terminal, interpreter, and file paths belong to Linux.

### Step 3.8 — End-to-end test

Create a harmless test project under `~/projects`, run it through VS Code connected to WSL, and record the verified environment state.

## Minimum-change rule

Do not reinstall, unregister, convert, or delete a Linux distribution merely to obtain a clean setup. First inspect the existing state and preserve any useful files. `wsl --unregister` is destructive and is not part of the normal setup path.

## Scope boundary

Step 3 covers the operating environment and a basic VS Code connection test. Extension selection, editor profiles, Jupyter configuration, Docker tooling, and automatic AI-completion controls belong to Step 4 unless they are strictly required to establish the initial WSL connection.
