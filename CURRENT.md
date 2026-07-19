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

Set up a lightweight Obsidian knowledge system for:

- concepts;
- finance;
- AI engineering;
- mathematics;
- MScFE learning;
- books and papers;
- research;
- maps of content.

Do not add LLM integration in Career OS v1.

## Completion condition

Step 6 is complete only when one completed MScFE concept is:

1. captured in the vault;
2. connected to relevant concepts or maps;
3. retrievable through a simple, repeatable navigation or search path;
4. reviewed for clarity, usefulness, and privacy;
5. supported by a lightweight vault standard recorded in the Career OS repository.

## Privacy architecture

The Obsidian vault must not be assumed to belong inside the public Career OS repository.

The design must preserve these boundaries:

- raw WQU course materials and active graded work remain private;
- private paper drafts, reviewer correspondence, personal data, health information, credentials, and confidential work remain outside the public repository;
- only public-safe architecture, conventions, templates, and operating guidance may be committed to `career-os`;
- storage, backup, and sync decisions must be reviewed before creating or moving a vault.

## Step 6 execution model

1. **Step 6 activation: complete.** Create `setup/step-6` from the verified Step 5 checkpoint and record the authorised objective.
2. **Step 6.1: not authorised.** Inventory existing Obsidian installation, vaults, storage, sync, devices, and note-taking constraints.
3. **Step 6.2: not authorised.** Design the minimum vault architecture, note types, naming, links, metadata, maps, private boundaries, and backup approach.
4. **Step 6.3: not authorised.** Create the vault and minimum folder or navigation structure without unnecessary plugins or LLM integration.
5. **Step 6.4: not authorised.** Capture, connect, and retrieve one completed MScFE concept using Ayush's first attempt.
6. **Step 6.5: not authorised.** Review the system, record the public-safe standard, open and merge one Step 6 pull request, and complete cleanup.

Substeps may be refined after Step 6.1 inventory, but later implementation must not begin early.

## Step 6.1 objective

Establish the actual starting state before choosing an architecture.

The inventory should determine:

- whether Obsidian is installed on Windows;
- whether any existing vaults contain useful or sensitive material;
- intended devices and operating systems;
- preferred local storage location;
- current or planned sync and backup mechanisms;
- whether the vault should be one general vault or another deliberately justified arrangement;
- current handwritten, Markdown, book-note, paper-note, and MScFE workflows;
- what information must remain private;
- the first eligible completed MScFE concept for the completion test.

No software installation, vault creation, file movement, sync configuration, plugin installation, or note migration is authorised during Step 6.1.

## Step 5 closure evidence

- PR #26 merged through merge commit `46a67c99222a87ce2632fbf019ad38cae6c6aa69`.
- Issue #25 closed automatically as completed.
- GitHub deleted `setup/step-5` automatically.
- The remote-tracking branch was pruned.
- The local setup branch was deleted normally.
- The canonical checkout returned to clean `main` at `357f04d2616e853af9ee362e0666b63e2e0957f7` with zero ahead and behind counts.
- The approved workflow is stored in `standards/git-github-workflow.md`.

## Known non-blocking observation

`code .` can still fail intermittently in WSL with a Windows executable interoperability error. This observation does not block the Obsidian inventory. Do not introduce an unrelated workaround on the Step 6 branch.

## Governing constraints

- Health, sleep, exercise, coursework, and recovery take priority over optional progress.
- No guilt debt applies.
- Plan detailed work only for the next two to three days.
- Prefer one coherent outcome per session.
- Use questions and Ayush's first attempt for conceptual learning work.
- Environment setup may use detailed beginner-safe instructions.
- Do not optimise for issue, branch, pull-request, commit, note, link, plugin, vault, streak, or hour counts.
- Prefer a small, understandable system over a comprehensive taxonomy.
- Never commit raw WQU materials, active graded work, employer or client confidential information, private datasets, credentials, API keys, SSH private keys, private health information, or uncleared private paper drafts.
- Step 7 remains unauthorised.

## Research and PhD direction

Potential PhD preparation and publication-quality research remain binding Career OS requirements.

The knowledge system should support prerequisite maps, paper reading, reproduction notes, comparison, limitations, and reusable public-safe insights without turning the vault into a publication-count system.

The full research and paper-development workflow remains in scope for Step 9.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, coursework, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

Step 6.1 requires explicit approval. There is no Step 6 activation blocker.

## Next action

Synchronise the canonical local checkout from `main` to `setup/step-6`, verify the activation commit and clean branch state, then stop for the exact instruction:

```text
Proceed to Step 6.1
```
