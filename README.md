# General Expert Agents

A governed source workspace for a reusable expert-agent fleet that is authored here and can now be loaded either as a local plugin source or deployed into the live Claude Code runtime.

---

## Purpose

This workspace exists to keep expert-agent behavior governable instead of editing runtime copies directly in `<user-runtime-agents>/`.

It is responsible for:
- managed source-of-truth authoring
- per-agent ownership and routing boundaries
- sync discipline from source to runtime
- validation evidence for routing behavior
- explicit operator policy when routing behavior is environment-dependent

---

## Path notation

- `<repo-root>` = this standalone repo root and the preferred public source-side path for install commands
- `<workspace-root>` = the current local working copy of the same package
- `<user-runtime-agents>` = the user-level Claude Code runtime agent directory
- `<user-runtime-skills>` = the user-level Claude Code runtime skill directory

## Installation and activation

### Recommended public install path
This package now has its own standalone GitHub repo at:
- `https://github.com/DarKWinGTM/general-expert`

Clone once, then run the install from the repo root:

```bash
git clone https://github.com/DarKWinGTM/general-expert.git
cd general-expert
claude plugins marketplace add ./ --scope local
claude plugins install general-expert@general-expert --scope local
```

Optional reload:

```bash
/reload-plugins
```

Check installed state:

```bash
claude plugins list
claude agents
```

Checked local validation from the repo root:
- `claude plugins marketplace add ./ --scope local` succeeds
- `claude plugins install general-expert@general-expert --scope local` succeeds
- `claude agents` shows the full `general-expert:*` fleet

### Update an installed plugin

If the plugin is already installed, update it by using the installed identifier shape `plugin@marketplace`:

```bash
claude plugins update general-expert@darkwingtm --scope local
```

Why this exact shape matters:
- `claude plugins update general-expert --scope local` may fail because the installed local plugin is keyed by `general-expert@darkwingtm`
- the explicit `plugin@marketplace` form matches the installed identifier shown in `claude plugins list`

### Alternate activation paths

| Path | Current meaning | Status |
|---|---|---|
| `claude --plugin-dir "<repo-root>"` | local plugin-source loading for the same governed fleet from the standalone repo | verified locally |
| sync to `<user-runtime-agents>/` | deployed runtime-copy path for the fleet | historical/current runtime path |
| `claude plugins marketplace add ./ --scope local` + `claude plugins install general-expert@general-expert --scope local` | repo-root local marketplace install for the standalone repo | validated locally |

### Local development compatibility note

The same fleet may still be referenced through the shared local `darkwingtm` marketplace during workspace development, but that route is no longer fleet authority. The standalone repo is now the intended source of truth, and any remaining shared-workspace usage should be treated as temporary local compatibility only.

## Source of Truth and Runtime Target

### Governed source workspace

```text
<workspace-root>/
```

### Active runtime deployment target

```text
Claude plugin cache + local settings via marketplace install
```

The old loose-file deployment target under `<user-runtime-agents>/` is now retired for this fleet.

### Authority rule

- `general-expert/agents/*.md` = governed source agent files
- `<user-runtime-agents>/*.md` = deployed runtime copies only
- design / changelog / TODO / phase / patch govern the source layer
- direct runtime edits should be back-ported into the governed source immediately

---

## Managed Fleet

| Agent | Primary Ownership | Current Routing Policy Snapshot |
|------|--------------------|---------------------------------|
| `nodejs-expert` | Node runtime, tooling, platform behavior | Explicit validation win for runtime/tooling prompts |
| `nodejs-backend-expert` | Node backend services, APIs, auth, DB, queues | Prefer explicit invocation in this environment |
| `bun-expert` | Bun runtime, tooling, compatibility, workflow | Broader operator policy still being closed |
| `bun-backend-expert` | Bun-native backend architecture and APIs | Explicit validation win for Bun backend architecture prompts |
| `html-css-js-frontend-expert` | Browser platform, semantic HTML, CSS, vanilla JS | Broader operator policy still being closed |
| `react-frontend-expert` | React frontend, TSX, hooks, state, hydration | Direct hydration-debug validation win recorded |
| `python-backend-expert` | Python backend services, APIs, auth, DB | Prefer explicit invocation in this environment |

---

## Artifact Roles

| Artifact | Role |
|----------|------|
| `README.md` | Workspace operator entrypoint |
| `.claude-plugin/plugin.json` | Plugin-compatible packaging metadata for the same fleet workspace |
| `agents/*.md` | Fleet runtime authority files |
| `design/design.md` | Fleet-level architecture and governance authority |
| `design/*.design.md` | Per-agent design authority |
| `changelog/changelog.md` | Fleet-level shipped/synchronized history |
| `changelog/*.changelog.md` | Per-agent shipped/synchronized history |
| `TODO.md` | Execution tracking only |
| `phase/SUMMARY.md` | Live execution summary and phase map |
| `phase/phase-*.md` | Governed execution detail per phase |
| `patch/*.patch.md` | Before/after evidence surface for governed changes |

### Phase vs patch

- **phase** = execution structure, scope, checklist, exit criteria
- **patch** = before/after comparison and evidence surface
- **changelog** = completed or synchronized history only
- **TODO** = unresolved execution work only

---

## Current Phase Model

### Historical baseline family
- `phase-010-governance-baseline.md`
- `phase-020-per-agent-design-baseline.md`
- `phase-030-per-agent-changelog-baseline.md`
- `phase-040-runtime-sync.md`
- `phase-050-validation.md`

### Current hardening family
- `phase-060-governance-reconciliation.md`
- `phase-070-runtime-overlay-governance.md`
- `phase-080-routing-policy-closure.md`
- `phase-090-multilingual-routing-interpretation.md`
- `phase-100-plugin-compatible-fleet-layout.md`

### Patch family

The patch layer lives in:

```text
patch/*.patch.md
```

Current active patch set:
- `patch/phase-040-runtime-sync.patch.md`
- `patch/phase-050-validation-round-1.patch.md`
- `patch/phase-055-backend-specialist-policy.patch.md`
- `patch/phase-060-governance-reconciliation.patch.md`
- `patch/phase-070-runtime-overlay.patch.md`
- `patch/phase-080-frontend-runtime-routing-policy.patch.md`
- `patch/phase-090-multilingual-routing-interpretation.patch.md`
- `patch/phase-100-plugin-compatible-fleet-layout.patch.md`

---

## Runtime Overlay Note

This workspace governs **7 managed agents only**.

However, observed routing behavior in the live runtime can also be influenced by co-resident agents outside this workspace, especially when they are installed in the same `<user-runtime-agents>/` directory.

Current notable co-resident agents include:
- `multi-hat-system.md`
- `prompt-optimizer.md`
- `generative-media-navigator.md`

Practical meaning:
- source parity for the managed fleet can be true
- while routing behavior is still shaped by a larger runtime environment

That distinction matters when interpreting routing-validation evidence.

---

## Current Governance State

Already established:
- governed source workspace for the 7-agent fleet
- per-agent design and changelog authority
- first source-to-runtime sync for managed agents
- first routing validation matrix
- explicit-invocation policy for `nodejs-backend-expert` and `python-backend-expert`
- patch baseline for sync, validation, policy, and governance reconciliation evidence
- plugin-compatible layout with `agents/` plus `.claude-plugin/plugin.json`
- verified local plugin-source loading through `--plugin-dir`
- shared local marketplace scaffolding also exposes this fleet for checked workspace development, but that is no longer the recommended public install story
- repo-root local marketplace install is now validated for the standalone package
- plugin visibility remains intact after `/reload-plugins`
- fresh CLI-process visibility confirms the marketplace-installed fleet remains available across session restarts

Still open:
- validate whether multilingual intent-oriented routing wording improves specialist matching without adding new collisions
- decide whether any routing wording needs to be narrowed after live testing
- decide when the deployed-copy path under `<user-runtime-agents>/` should be retired after marketplace-installed usage remains stable
- polish public-repo readiness while keeping `@darkwingtm` as the current shared publisher namespace

---

## Recommended Operator Use

### Use explicit invocation when specialist behavior matters most for
- `nodejs-backend-expert`
- `python-backend-expert`

### Accept current validated specialist-first routing for
- `nodejs-expert`
- `bun-backend-expert`
- direct hydration/debug work via `react-frontend-expert`

### Treat these domains as still under active policy closure
- Bun runtime prompts
- browser-platform prompts
- broader React prompt families outside the validated direct hydration-debug shape

---

## Workspace Checklist

Use this workspace correctly when:
- source files are edited here first
- runtime copies are treated as deployed artifacts, not primary authority
- phase files describe execution state
- patch files show before/after evidence
- changelog records completed/synchronized outcomes only
- TODO carries unresolved work only

---

## Current Review Questions

1. Is runtime-overlay interpretation now explicit enough for routing evidence?
2. Are Bun / browser / React operator policies explicit enough to stop ambiguity?
3. Does the patch layer now make sync and validation history reviewable enough?
4. Do fleet-level and per-agent artifacts now stay aligned after follow-up closure?
