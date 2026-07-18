# Current State

_Last updated: 2026-07-18_

## Operating mode

**Career OS setup mode**

Steps 1, 2, 3, and 4 are complete.

No setup step is active. Step 5 has not been authorised.

## Current objective

Preserve the validated VS Code, WSL, and Dev Container engineering environment and wait for the exact instruction:

```text
Proceed to Step 5
```

Do not start the Git and GitHub practice workflow before that gate.

## Repository state

- Repository: `Harper2123/career-os`
- Step 4 branch: `setup/step-4`
- Step 4 closure pull request: `#24`
- Base branch: `main`
- Canonical local checkout: `/home/akcoo/projects/career-os`
- Canonical checkout filesystem: `ext4`
- Canonical checkout owner: `akcoo:akcoo`
- Canonical origin: `git@github.com:Harper2123/career-os.git`

The Step 4 branch was verified clean, matched its remote exactly, and was 44 commits ahead of `main` immediately before the final `CURRENT.md` closure update.

After pull request #24 is merged, the local checkout must be moved to clean, up-to-date `main`, and the merged local setup branch must be deleted. GitHub is configured to delete merged head branches automatically.

## Step 4 completion result

### Architecture

- Windows remains the editor host.
- Ubuntu under WSL 2 is the primary Linux source workspace.
- Active Linux-developed repositories belong under `/home/akcoo/projects` on `ext4`.
- Windows VS Code uses the dedicated `Career OS Engineering` Empty Profile.
- Substantial Python projects use repository-owned Dev Containers.
- Ubuntu system Python remains limited to operating-system diagnostics and lightweight host checks.
- Project dependencies are not installed into Ubuntu system Python.
- Jupyter is available only when notebook work is justified by the repository.

### Career OS Engineering profile

```text
Profile ID: -639a60a5
Career OS extension count: 15
Default extension count: 36
Default settings hash: e5ffc83c78e5ade86a903ef0a45b660b2c65af6eb6c300e8aa92d86cda110389
Career OS settings hash: 6218b6bfbdef3903c476c58172d007c12199f1d89dc557dae3a408b9f662dd6
```

Verified boundaries:

- no Windows Python interpreter in the Career OS profile;
- no global Python test framework;
- no terminal profile selection;
- no global Ruff rule configuration;
- no custom keybindings;
- Settings Sync unchanged;
- `terminal.integrated.initialHint=false` accepted as cosmetic.

### Automatic-AI boundary

The following settings are enforced in both the Default and Career OS profiles:

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
- no user-installed Copilot extension exists in the Career OS profile;
- no Copilot package exists in the WSL user-extension registries.

### Accepted WSL baseline

```text
WSL machine settings hash: 6e07e3fb3ad01cb91ec0c80b6f5039195b9409a1217c573036671004d7cbfc52
Global WSL extension registry hash: bd153de267f4e53def8f4e625c6f358bc265e165df1fcaac2da86b30cbbd4efe
WSL extension-directory-name hash: 884e20856f1c296b51250d17e33df8d36f19411983cceead7f18c8f08d4f8c9a
WSL remote-profile-directory-name hash: 9df76246b160eca49529b04d2c21066694590430729054030fd4ad29a143d0ac
All WSL extension registries hash: 7f628e9c0cb74a45fd0a7cb9bb78070802aa0ba2363e452861bc07f3ae3be68a
```

### Proved workflows

The environment successfully performed:

- Windows VS Code connection to Ubuntu WSL;
- Bash terminal work in the Linux workspace;
- Python navigation, diagnostics, Ruff formatting, and execution;
- repository-owned unittest discovery and execution;
- Markdown linting and built-in preview;
- Git inspection and Source Control diffs;
- GitHub Pull Requests view access;
- Container Tools inventory;
- repository-owned Dev Container creation and connection;
- isolated container Python at `/usr/local/bin/python`;
- pinned `ipykernel==7.3.0` inside the disposable container environment;
- notebook execution using the container Python kernel;
- exact restoration of temporary editor changes;
- deliberate manual Chat without automatic AI suggestions.

### Cleanup result

Removed only after exact identity, ownership, repository, state, image, and reference guards passed:

- `/home/akcoo/projects/career-os-vscode-wsl-check`;
- validation container `cc661a3a5f490450893f9658b36cb2fde10c42f1f8fd71bccdc85d61467a24ce`;
- validation image `sha256:4025f17533ee4a3b2ac50ca6d42af180a4fa98463c14f3fea24f3e239739e49c`.

No Docker prune, volume deletion, extension deletion, profile deletion, host package installation, unrelated-resource deletion, remote creation, or fixture push occurred.

## Known non-blocking observations

### WSL interoperability

WSL-to-Windows executable interoperability disappeared more than once during Step 4. Windows process checks should run in Windows PowerShell, and Ubuntu preservation checks should remain Linux-only. No persistent workaround was added.

### Ruff disposable-fixture observation

The container formatter reformatted the function signature but did not add spaces around `+` in one intentionally compressed return expression during the observed save. Ruff diagnostics and formatter invocation were independently proven. This does not block the environment.

## Durable standard

The approved and validated environment architecture is recorded in:

```text
standards/vscode-environment.md
```

Future additions require a demonstrated project need or observed friction. Do not expand the editor baseline merely for completeness.

## MScFE state

- Next course: Derivative Pricing
- Confirmed start date: **2026-07-21**
- Health, sleep, course work, and recovery take priority
- Unrelated personal AI engineering is capped at approximately 3 to 4 hours per week during the active course
- No guilt debt applies

## Immediate blocker

Step 5 requires explicit approval. There is no technical Step 4 blocker.

## Next action

Complete the local post-merge synchronisation for pull request #24, then stop and wait for:

```text
Proceed to Step 5
```
