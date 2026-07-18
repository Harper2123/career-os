# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, and 3 are complete. Step 4 is in final closure.

## Active setup branch

- Repository: `Harper2123/career-os`
- Working branch: `setup/step-4`
- Base branch: `main`
- Step 4 pull request has not yet been created.
- Step 5 must not begin until Step 4.7 is complete.

## Current task

**Step 4.7 is active. Checkpoint A is partially complete.**

Checkpoint A has already proved:

- all five automatic-AI controls are disabled in both the Default and `Career OS Engineering` profiles;
- `chat.disableAIFeatures` is unset in both profiles;
- the Career profile contains exactly fifteen approved extensions;
- no user-installed Copilot extension exists in that profile;
- the live WSL editor probe showed no ghost text, next-edit proposal, automatic rename proposal, or AI-labelled code action;
- deliberate manual Chat remained available;
- all accepted Windows and WSL settings and extension hashes remained unchanged;
- the disposable fixture, stopped validation container, and generated validation image passed their deletion guards.

The guarded cleanup script stopped before deleting anything because it compared the full 64-character container ID with the 12-character short ID returned by `docker ps -aq`:

```text
expected: cc661a3a5f490450893f9658b36cb2fde10c42f1f8fd71bccdc85d61467a24ce
actual:   cc661a3a5f49
```

This is a verification-script defect only. Container identity, stopped state, image identity, and exclusive image reference count had already passed. Because `set -e` stopped before the deletion section:

- the disposable fixture still exists;
- container `cc661a3a5f490450893f9658b36cb2fde10c42f1f8fd71bccdc85d61467a24ce` still exists and is exited;
- image `sha256:4025f17533ee4a3b2ac50ca6d42af180a4fa98463c14f3fea24f3e239739e49c` still exists;
- no Docker resource, fixture, extension, profile, repository, or user file was deleted;
- the local Career OS checkout was not yet synchronised by the cleanup script.

The next action is one corrected guarded continuation that normalises the container-reference ID to its full form, deletes only the three authorised disposable resources, and synchronises the local Career OS checkout to `setup/step-4`.

Checkpoint B remains blocked until that continuation passes.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: complete.** Consolidated container workflow and preservation.
7. **Step 4.7: active.** Checkpoint A cleanup continuation pending, then repository review, pull request, merge, and branch cleanup.

## Accepted Windows baseline

```text
Default settings hash: e5ffc83c78e5ade86a903ef0a45b660b2c65af6eb6c300e8aa92d86cda110389
Career OS settings hash: 6218b6bfbdbef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
Career OS profile ID: -639a60a5
Career OS extension count: 15
Default extension count: 36
```

Automatic-AI settings:

```json
{
  "editor.inlineSuggest.enabled": false,
  "github.copilot.enable": {
    "*": false
  },
  "github.copilot.nextEditSuggestions.enabled": false,
  "github.copilot.renameSuggestions.triggerAutomatically": false,
  "github.copilot.editor.enableCodeActions": false
}
```

`chat.disableAIFeatures` remains unset. `terminal.integrated.initialHint=false` is accepted as a cosmetic preference.

## Accepted WSL baseline

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

## Disposable Step 4 resources

Fixture:

```text
Path: /home/akcoo/projects/career-os-vscode-wsl-check
Branch: main
Head: fe5e9f30ce7301f833818fd4c24b33e19695846a
Commit count: 2
Tracked files: 12
Remotes: 0
Worktree: clean
Tree hash: 806cfdb2cc35b2f86327a6e6a7a1068ffdd11ae0bf0fa4189677fa2649f982c5
```

Docker:

```text
Container ID: cc661a3a5f490450893f9658b36cb2fde10c42f1f8fd71bccdc85d61467a24ce
Container state: exited
Image ID: sha256:4025f17533ee4a3b2ac50ca6d42af180a4fa98463c14f3fea24f3e239739e49c
```

Only these three disposable resources are authorised for deletion. No prune or volume deletion is authorised.

## Known non-blocking issues for final acceptance

### WSL interoperability

WSL-to-Windows executable interoperability disappeared more than once during Step 4. Use Windows PowerShell for Windows process checks and Linux-only Ubuntu preservation scripts. Do not add a persistent workaround during Step 4.

### Ruff observation

The container formatter reformatted the function signature but did not add spaces around `+` in the intentionally compressed return expression during the observed save. Ruff diagnostics and format-on-save activation were proven. Record this as minor non-blocking evidence.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, course work, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

One corrected guarded Checkpoint A cleanup and local-repository synchronisation continuation.

## Stop rules

Until that continuation passes:

- keep VS Code closed;
- leave Docker Desktop running;
- do not edit the fixture;
- do not remove any Docker resource manually;
- do not prune Docker;
- do not create or merge the Step 4 pull request;
- do not begin Step 5.
