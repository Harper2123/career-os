# Current State

_Last updated: 2026-07-19_

## Operating mode

**Career OS setup mode**

Steps 1 through 5 are complete. Step 6 is active.

## Active setup branch

- Repository: `Harper2123/career-os`
- Working branch: `setup/step-6`
- Base branch: `main`
- Base checkpoint: `357f04d2616e853af9ee362e0666b63e2e0957f7`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- `main` remains the last merged top-level checkpoint.
- One pull request will cover the complete top-level Step 6 under Decision 0002.
- Unrelated work must not be added to this branch.

## Current objective

Set up a lightweight Obsidian knowledge system for concepts, finance, AI engineering, mathematics, MScFE learning, books, papers, research, and maps of content.

Do not add LLM integration in Career OS v1.

## Completion condition

Step 6 is complete only when one completed MScFE concept is:

1. captured in the vault;
2. connected to relevant concepts or maps;
3. retrievable through a simple, repeatable navigation or search path;
4. reviewed for clarity, usefulness, and privacy;
5. supported by a lightweight, public-safe vault standard recorded in the Career OS repository.

## Current task

**Step 6.1 is complete. Step 6.2 has not been authorised.**

Do not design the final architecture, create a vault, move files, configure sync or backup, install plugins, create templates, or write the completion-test note before the exact instruction:

```text
Proceed to Step 6.2
```

## Step 6 execution model

1. **Step 6 activation: complete.** Create `setup/step-6` from the verified Step 5 checkpoint and record the authorised objective.
2. **Step 6.1: complete.** Inventory the Obsidian installation, vaults, devices, storage, sync, backup, note-taking state, privacy constraints, and completion-test concept.
3. **Step 6.2: not authorised.** Design the minimum vault architecture, storage location, backup approach, note types, naming, links, metadata, maps, and private boundaries.
4. **Step 6.3: not authorised.** Create the vault and minimum navigation structure without unnecessary plugins or LLM integration.
5. **Step 6.4: not authorised.** Capture, connect, and retrieve one completed MScFE concept using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review the system, record the public-safe standard, open and merge one Step 6 pull request, and complete cleanup.

Substeps may be refined after the Step 6.2 design, but later implementation must not begin early.

## Step 6.1 inventory result

### Obsidian installation

- Obsidian is installed on Windows and launches successfully.
- Version: `1.12.7`
- Installer version: not shown on the initial screen.
- Automatic-update state: not available before opening a vault.
- Signed into Obsidian account: no.
- Obsidian Sync: not configured.
- Existing vaults registered in Obsidian: none.
- Existing Obsidian vaults or Markdown note folders reported by Ayush: none.
- Existing vault-specific plugin, link, attachment, deletion, and file-location settings: not applicable.

### Intended devices

- Windows laptop: required.
- Android phone: useful but optional.
- Work computer: must not access the vault.
- The Step 6 architecture must be Windows-first and must not depend on Android access.

### Sync and backup state

- Documents is not managed by OneDrive.
- No other sync tool is currently used.
- No backup method currently exists.
- No prior cloud-sync conflicts are known.
- Paid Obsidian Sync is not acceptable.
- A free backup approach must be designed before the vault is created.
- Optional Android access must not force a fragile or high-maintenance sync architecture.

### Current note-taking state

- No established handwritten, Markdown, MScFE, book, paper, code, or research-note workflow currently exists.
- No migration burden exists.
- The design should begin with the smallest useful system rather than recreating a complex taxonomy.

## Accepted privacy classification

### Public-safe material

Suitable for the public Career OS repository when intentionally prepared for publication:

- Ayush's own concept explanations;
- Ayush's own mathematical derivations;
- public paper citations;
- paper summaries written in Ayush's own words;
- public-safe templates, conventions, and knowledge-system guidance.

Public-safe does not mean that every such note must be published. Publication remains deliberate.

### Private personal vault

Suitable for the private Obsidian vault:

- personal study notes;
- completed-course concept notes;
- book notes;
- paper-reading notes;
- non-confidential research ideas;
- personal learning reflections.

### Outside both the public repository and the general vault

- raw WQU PDFs and course materials;
- active graded questions and submissions;
- employer or client information;
- credentials, recovery codes, encryption secrets, and private keys;
- personal health records;
- private paper drafts and reviewer correspondence unless a separately reviewed private research location is approved.

## Completion-test concept

The accepted Step 6 validation concept is:

```text
Concept: Weak stationarity
Completed course: Financial Econometrics
Related concept 1: Autocovariance and autocorrelation
Related concept 2: Unit roots and non-stationarity
```

Why it is a suitable test:

- it is already studied rather than part of the upcoming live course;
- it is narrow enough for one coherent concept note;
- it has a precise mathematical definition;
- it supports an example and counterexample;
- it links naturally to multiple time-series concepts;
- it can test capture, linking, navigation, search, and retrieval without exposing graded work.

The concept note must not be written until Step 6.4.

## Accepted design constraints

- Windows-first.
- Offline-first.
- Free sync and backup only.
- Android access is optional.
- No access from the work computer.
- Minimal maintenance.
- No community plugins initially.
- No LLM integration.
- Prefer one general personal knowledge vault unless Step 6.2 identifies a concrete privacy or operational reason to separate it.
- Prefer understandable folders, links, and maps over elaborate metadata or automation.
- Do not optimise for note, link, folder, tag, plugin, or vault counts.

## Privacy architecture

The actual Obsidian vault is private and must not be placed inside the public Career OS repository.

Only public-safe architecture, conventions, templates, and operating guidance may be committed to `career-os`.

Storage and backup must be designed before creating the vault because no backup currently exists. Sync and backup are separate concerns and must not be treated as interchangeable.

## Step 6.2 design questions

The next authorised unit must decide:

- the Windows vault location;
- one-vault versus multi-vault architecture;
- the minimum folder and navigation structure;
- note types and naming conventions;
- minimal metadata, links, and maps of content;
- attachment handling;
- deletion behaviour;
- a free backup method;
- whether optional Android access should be deferred or supported now;
- which built-in Obsidian features are sufficient without community plugins;
- how public-safe insights may later move deliberately from the private vault to GitHub without copying restricted material.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This observation does not block Obsidian design. Do not introduce an unrelated workaround on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority over optional progress.
- No guilt debt applies.
- Plan detailed work only for the next two to three days.
- Prefer one coherent outcome per session.
- Use questions and Ayush's first attempt for conceptual learning work.
- Environment setup may use detailed beginner-safe instructions.
- Never commit raw WQU materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Research work must favour reproducibility, traceable decisions, experiment evidence, and separation of exploratory notes from reusable tested modules.
- Step 7 remains unauthorised.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, coursework, and recovery take priority.
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course.
- No guilt debt applies.

## Immediate blocker

Step 6.2 requires explicit approval. There is no Step 6.1 inventory blocker.

## Next action

Synchronise the canonical local checkout to the latest `setup/step-6` remote commit, verify a clean zero-ahead and zero-behind state, and stop for the exact Step 6.2 gate.
