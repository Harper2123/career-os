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

**Step 4.7 is active. Checkpoint A is complete. Checkpoint B is active.**

Checkpoint A proved the automatic-AI boundary, validated the final Windows and WSL baselines, and removed only the explicitly disposable Step 4 fixture, validation container, and validation image.

A read-only checkout discovery found no existing local clone of `Harper2123/career-os` in the searched Linux and Windows roots:

```text
career_os_matching_checkout_count=0
career_os_local_checkout=ABSENT
step_4_7_checkout_discovery=COMPLETE
```

This is not an environment failure. Checkpoint B must now establish the canonical local checkout at:

```text
/home/akcoo/projects/career-os
```

The clone must initially track `setup/step-4`, remain clean, and match the remote branch exactly. After that checkpoint passes, the durable VS Code standard and `CURRENT.md` will be finalised, the Step 4 pull request will be created and reviewed, and the repository will be merged and cleaned up.

## Step 4 status

1. **Step 4.1: complete.** Existing Windows and WSL VS Code inventory.
2. **Step 4.2: complete.** Minimum profile, extension, runtime, and AI-boundary architecture.
3. **Step 4.3: complete.** Windows `Career OS Engineering` profile.
4. **Step 4.4: complete.** WSL continuity, extension scope, terminal, settings, interpreter boundaries, and preservation.
5. **Step 4.5: complete.** Consolidated editor workflows and preservation.
6. **Step 4.6: complete.** Consolidated container workflow and preservation.
7. **Step 4.7: active.** Checkpoint A complete; canonical local clone, durable review, pull request, merge, and branch cleanup remain.

## Checkpoint A acceptance

### Automatic-AI boundary

Passed in both the Default and `Career OS Engineering` profiles:

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

Also verified:

- `chat.disableAIFeatures` is unset;
- deliberate manual Chat remains available;
- no ghost text appeared;
- no next-edit proposal appeared;
- no automatic rename proposal appeared;
- no AI-labelled code action appeared;
- the Career profile contains exactly fifteen approved extensions;
- no user-installed Copilot extension exists in that profile.

### Accepted Windows baseline

```text
Default settings hash: e5ffc83c78e5ade86a903ef0a45b660b2c65af6eb6c300e8aa92d86cda110389
Career OS settings hash: 6218b6bfbdbef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
Career OS profile ID: -639a60a5
Career OS extension count: 15
Default extension count: 36
```

`terminal.integrated.initialHint=false` is accepted as a cosmetic profile preference.

### Accepted WSL baseline

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

### Disposable-resource cleanup

Removed after exact identity and state guards passed:

- `/home/akcoo/projects/career-os-vscode-wsl-check`;
- stopped validation container `cc661a3a5f490450893f9658b36cb2fde10c42f1f8fd71bccdc85d61467a24ce`;
- generated validation image `sha256:4025f17533ee4a3b2ac50ca6d42af180a4fa98463c14f3fea24f3e239739e49c`.

No Docker prune, volume deletion, extension deletion, profile deletion, package installation, unrelated-resource deletion, remote creation, or fixture push occurred.

## Known non-blocking issues

### WSL interoperability

WSL-to-Windows executable interoperability disappeared more than once during Step 4. Use Windows PowerShell for Windows process checks and Linux-only Ubuntu preservation scripts. Do not add a persistent workaround during Step 4.

### Ruff observation

The container formatter reformatted the function signature but did not add spaces around `+` in the intentionally compressed return expression during the observed save. Ruff diagnostics and format-on-save activation were proven. Record this as minor non-blocking evidence rather than extending setup.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, course work, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

Establish and verify the canonical local Career OS checkout on `setup/step-4` without modifying repository content.

## Stop rules

Until that checkout passes:

- keep VS Code closed;
- leave Docker Desktop running;
- do not create or merge the Step 4 pull request manually;
- do not begin Step 5.
