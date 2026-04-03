# General Expert Agents Design

> **Current Version:** 0.6.0
> **Last Updated:** 2026-04-04
> **Status:** Active - Standalone Repo Authority
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 0. Document Control

> **Parent Scope:** TEMPLATE / PLUGIN / general-expert
> **Design Type:** Agent Fleet Architecture + Governance
> **Runtime Target:** marketplace-installed plugin cache + local settings, with `<user-runtime-agents>/` only when the deployed-copy path is intentionally reused
> **Source of Truth:** `<repo-root>/`

---

## 1. Path notation

- `<repo-root>` = this standalone repo root and the preferred public source-side path for install commands
- `<workspace-root>` = the current local working copy of the same package
- `<user-runtime-agents>` = the user-level Claude Code runtime agent directory
- `<user-runtime-skills>` = the user-level Claude Code runtime skill directory

## 2. Purpose

This document defines the design baseline for the reusable expert-agent fleet governed from `<repo-root>/`.
The active package now includes a dedicated routing skill front door so fleet usage can start from an operator-facing selection surface rather than agent-name recall only.
The intended use is bounded: it should guide specialist choice and explicit-invocation posture, not become a competing runtime authority.

The goal is to manage these agents as governed source artifacts before deployment to the active Claude Code runtime directory.

This chain should answer:
- what each managed agent owns
- what each managed agent defers
- how routing boundaries are kept clean
- how the standalone repo remains the governed fleet authority
- how source files are synchronized into `<user-runtime-agents>/` only when that deployed-copy path is still intentionally needed
- how the same governed fleet is loaded through a plugin-compatible path
- how routing evidence is interpreted in the real runtime environment
- how changes are tracked through README, changelog, TODO, phase, and patch artifacts

---

## 2. Source-of-Truth Model

### 2.1 Authoring location

Governed source files live in:

```text
<repo-root>/
```

### 2.2 Runtime deployment location

The active runtime copies used by Claude Code now come from marketplace-installed plugin cache material plus local settings enablement.

Observed current-machine install path:

```text
~/.claude/plugins/cache/darkwingtm/general-expert/1.2.0/
```

The older loose-file deployment path under `<user-runtime-agents>/` is now retired for this fleet.

### 2.3 Authority rule

- `<repo-root>/agents/*.md` = governed source runtime definitions
- `<repo-root>/skills/routing/SKILL.md` = operator-facing routing support surface for the same governed fleet
- `<user-runtime-agents>/*.md` = deployed runtime copies only when the old loose-file path is still intentionally used
- `.claude-plugin/plugin.json` = plugin-compatible packaging metadata for the same governed fleet
- design/changelog/TODO/phase/patch govern the standalone repo source layer, not the deployed copy
- shared-workspace usage, when it still exists locally, is compatibility context only and not source authority

### 2.4 Sync rule

Direct runtime edits should be avoided.
If a runtime hotfix is applied in `<user-runtime-agents>/`, it must be back-ported into `<repo-root>/` immediately.

---

## 3. Agent Fleet Baseline

### 3.1 Current managed agents

- `agents/nodejs-expert.md`
- `agents/nodejs-backend-expert.md`
- `agents/bun-expert.md`
- `agents/bun-backend-expert.md`
- `agents/html-css-js-frontend-expert.md`
- `agents/react-frontend-expert.md`
- `agents/python-backend-expert.md`

### 3.2 Target taxonomy

| Agent | Primary Ownership |
|------|--------------------|
| `nodejs-expert` | Node runtime, tooling, platform behavior |
| `nodejs-backend-expert` | Node backend services, APIs, auth, DB, queues |
| `bun-expert` | Bun runtime, tooling, compatibility, workflow |
| `bun-backend-expert` | Bun-native backend architecture and APIs |
| `html-css-js-frontend-expert` | Web platform, semantic HTML, CSS, vanilla JS |
| `react-frontend-expert` | React frontend, TSX, hooks, state, hydration |
| `python-backend-expert` | Python backend services, APIs, auth, DB |

---

## 4. Authoring Contract

### 4.1 File format

Each agent file should use Claude Code custom agent structure:

```yaml
---
name: <agent-name>
description: <routing metadata>
tools: <comma-separated tools>
model: inherit
---
```

### 4.2 Description policy

The `description` field is routing metadata.
It should:
- say what the agent owns
- include key trigger phrases naturally
- include one clear exclusion sentence when overlap is likely

It should not:
- contain long transcripts
- contain commentary blocks
- duplicate the full operating prompt

### 4.3 Body policy

The body should be the operating prompt and should remain structured.
Preferred sections:
- `## Owns`
- `## Defers`
- `## Not for`
- `## Core Principles`
- `## Workflow`
- `## Verification Requirements`
- `## Output`

### 4.4 Tool policy

Tool scope should be deliberate and minimal.
Use explicit `tools:` in the file rather than depending on broad inheritance unless there is a clear reason not to.

### 4.5 Non-goals

This fleet should not introduce:
- overlapping catch-all descriptions
- undocumented frontmatter fields unless re-verified
- references to tools the user explicitly rejected

Current user-specific exclusion:
- do not introduce or recommend `mgrep`
- do not introduce or recommend `greptile`

---

## 5. Routing and Boundary Rules

### 5.1 Routing-first debug rule

If a prompt routes to the wrong agent:
- first refine the `description`
- then refine `## Defers` / `## Not for` if needed

### 5.2 Ownership split rule

Use platform/runtime agents for runtime/toolchain problems:
- `nodejs-expert`
- `bun-expert`

Use application-layer agents for backend/frontend implementation problems:
- `nodejs-backend-expert`
- `bun-backend-expert`
- `react-frontend-expert`
- `html-css-js-frontend-expert`
- `python-backend-expert`

### 5.3 Collision prevention rule

Adjacent agents must be able to answer these questions clearly:
- What do I own?
- What do I defer?
- What am I not for?

---

## 6. Sync Workflow Baseline

### 6.1 Standard path

1. Update design if behavior/scope changes
2. Update the governed source agent or skill file under `<repo-root>/agents/` or `<repo-root>/skills/`
3. Validate plugin-compatible loading from the same workspace when relevant
4. Validate repo-root local marketplace install with `claude plugins marketplace add ./ --scope local` when public local activation matters
5. Treat the shared `darkwingtm` route only as checked local workspace-development context when it is still useful
6. Sync source agent file to `<user-runtime-agents>/` only when the deployed-copy path is still intentionally needed
7. Validate discovery, routing, and routing-front-door behavior
8. Update changelog and TODO

### 6.2 Hotfix path

1. Apply urgent runtime fix in `<user-runtime-agents>/`
2. Back-port immediately into `<repo-root>/`
3. Record the hotfix in changelog and TODO history

### 6.3 Validation baseline

After sync:
- agent file exists in both source and runtime locations
- `claude agents` discovers the deployed copy
- prompt routing matches intended taxonomy closely enough to interpret confidently

---

## 7. Validation and Policy Model

### 7.1 Confirmed explicit specialist wins

Current evidence-backed wins include:
- `nodejs-expert` for Node runtime/module/tooling prompts
- `bun-backend-expert` for Bun-native backend architecture prompts
- direct hydration debugging via `react-frontend-expert`

### 7.2 Backend specialist governance decision

For the current Claude Code environment, the strongest evidence-backed working model is:
- `nodejs-backend-expert` and `python-backend-expert` should be treated as **explicit-invocation-oriented specialists**
- these backend specialists should not be treated as reliably delegation-first auto-routed agents for broad natural-language backend prompts
- attached file paths improve contextual precision, but do not by themselves guarantee explicit specialist delegation
- explicit invocation currently gives the most reliable specialist behavior for these two agents

### 7.3 Current multilingual-routing rule

For this fleet, multilingual prompt support should be implemented through **intent-oriented routing language in the `description` line** of the source runtime agent files.

This product wave now actively applies that rule across the managed fleet so routing metadata is clearer about task/domain intent even when the user prompt language changes.
The active policy remains: improve cross-language intent matching without translating the full runtime bodies.

Policy:
- keep the substantive agent body in English
- make routing language emphasize task intent and domain intent rather than exact wording or prompt language
- use multilingual examples in design/validation only where they materially improve testing clarity
- keep descriptions short enough that the routing metadata remains readable and useful
- narrow or revise wording if it creates collisions across adjacent specialists

---

## 8. Patch and Evidence Model

### 8.1 Patch location

Governed patch artifacts live in:

```text
patch/*.patch.md
```

### 8.2 Patch role

Use patch artifacts to show before/after evidence for:
- source-to-runtime sync proof
- routing validation evidence
- explicit policy changes
- governance reconciliation changes
- runtime-overlay interpretation changes

### 8.3 Phase-to-patch linkage rule

When a phase uses a governed patch artifact:
- `phase/SUMMARY.md` should name that patch explicitly
- the child phase file should name that patch explicitly in `Patch References`
- the patch should name its governing phase

### 8.4 Artifact boundary rule

- **phase** = execution structure, scope, checklist, exit criteria
- **patch** = before/after evidence surface
- **changelog** = completed or synchronized history only
- **TODO** = unresolved execution work only

---

## 9. Runtime Overlay Note

### 9.1 Managed-fleet truth

This workspace governs the 7 managed agents listed above.
For those managed files, source-of-truth control and runtime parity can be evaluated directly.

### 9.2 Overlay reality

Observed routing behavior in the live runtime may also be influenced by co-resident agents outside this workspace, especially when they are installed in the same `<user-runtime-agents>/` directory.

Current notable examples include:
- `multi-hat-system.md`
- `prompt-optimizer.md`
- `generative-media-navigator.md`

### 9.3 Interpretation rule

That means:
- source parity for the managed fleet can be true
- while routing evidence is still shaped by a larger live runtime environment

This workspace therefore governs:
- managed-file design truth
- managed-file sync truth
- routing interpretation guidance for the managed fleet
- plugin-compatible packaging and local marketplace installability for the same governed fleet

It does not claim that the runtime is a clean 7-agent-only test surface.

---

## 10. Governance Companions

| Document | Role |
|----------|------|
| `README.md` | Workspace operator entrypoint |
| `.claude-plugin/plugin.json` | Plugin-compatible packaging metadata |
| `skills/routing/SKILL.md` | Operator-facing routing front door for specialist selection |
| `agents/*.md` | Fleet runtime authority |
| `design/design.md` | Architecture and governance authority |
| `changelog/changelog.md` | Master shipped/synchronized history |
| `TODO.md` | Execution tracking |
| `phase/SUMMARY.md` | Live phased rollout summary when staged execution is needed |
| `patch/*.patch.md` | Before/after evidence surface for governed changes |

---

## 11. Next Design Expansions

Future additions can include:
- a routing debug sheet under `support/`
- a sync checklist under `support/`
- narrower policy guidance once Bun/browser/React closure work finishes
- richer operator guidance around the routing skill only if it stays support-facing rather than becoming a competing runtime authority

---

> **Design anchor:** governed source fleet first, runtime overlay interpreted explicitly, and phase/patch roles kept separate.