# Phase Summary - General Expert Agent Governance Rollout

> **Project:** General Expert Agents
> **Scope:** Governance baseline, source-of-truth model, sync discipline, routing validation, runtime-overlay interpretation, and policy reconciliation for the `general-expert` fleet
> **Status:** In Progress
> **Last Updated:** 2026-04-02

---

## Overall goal

Maintain a governed source workspace for the reusable expert-agent fleet in:

```text
<workspace-root>/
```

while keeping the active runtime deployment target in:

```text
<user-runtime-agents>/
```

The goal is not only to store agent files in one directory.
The goal is to keep a clean governance model that supports:
- source-of-truth authoring
- routing/taxonomy control
- changelog/TODO traceability
- patch-backed evidence for important changes
- repeatable sync from source to runtime
- plugin-compatible loading from the same governed workspace
- explicit interpretation of runtime behavior in a mixed live environment

---

## Source-input extraction table

| Phase | Phase File | Design Source | Patch Source | Derived Execution Work | Target Outcome |
|------|------------|---------------|--------------|-------------------------|----------------|
| P1 | `phase-010-governance-baseline.md` | `../design/design.md` sections: Source-of-truth model, governance companions | none | Establish master governance baseline for the fleet | One authoritative source workspace |
| P2 | `phase-020-per-agent-design-baseline.md` | `../design/*.design.md` plus `../design/design.md` fleet taxonomy | none | Establish per-agent design authority for all 7 managed agents | Each agent has its own governed design contract |
| P3 | `phase-030-per-agent-changelog-baseline.md` | `../changelog/*.changelog.md` plus `../changelog/changelog.md` | none | Establish per-agent change-history authority for all 7 managed agents | Each agent has its own governed changelog chain |
| P4 | `phase-040-runtime-sync.md` | `../design/design.md` section: Sync Workflow Baseline plus per-agent source files | `../patch/phase-040-runtime-sync.patch.md` | Define and execute repeatable source-to-runtime synchronization | Runtime copies stay aligned with governed source |
| P5 | `phase-050-validation.md` | `../design/design.md` section: Routing and Boundary Rules plus per-agent design targets | `../patch/phase-050-validation-round-1.patch.md`, `../patch/phase-055-backend-specialist-policy.patch.md` | Validate discovery and routing behavior using prompt tests against the synced runtime fleet | Agent routing becomes evidence-backed and maintainable |
| P6 | `phase-060-governance-reconciliation.md` | `../design/design.md` section: Patch and Evidence Model plus governance companions | `../patch/phase-060-governance-reconciliation.patch.md` | Reconcile README/design/changelog/TODO/phase state and add the initial patch baseline | Artifact roles and rollout state become audit-consistent |
| P7 | `phase-070-runtime-overlay-governance.md` | `../design/design.md` section: Runtime Overlay Note | `../patch/phase-070-runtime-overlay.patch.md` | Define how mixed-runtime behavior should be interpreted when unmanaged co-resident agents are present | Routing evidence remains honest about managed-fleet scope |
| P8 | `phase-080-routing-policy-closure.md` | `../design/design.md` section: Validation and Policy Model plus frontend/runtime per-agent designs | `../patch/phase-080-frontend-runtime-routing-policy.patch.md` | Close the current Bun/browser/React operator policy surface | Open routing-policy ambiguity is reduced to explicit operator guidance |
| P9 | `phase-090-multilingual-routing-interpretation.md` | `../design/design.md` section: multilingual routing policy plus all per-agent routing-intent sections | `../patch/phase-090-multilingual-routing-interpretation.patch.md` | Improve multilingual intent-oriented routing across specialist surfaces without translating full bodies | Specialist detection becomes easier to align and validate across prompt languages |
| P10 | `phase-100-plugin-compatible-fleet-layout.md` | `../design/design.md` source-of-truth model plus plugin-compatible workspace rules | `../patch/phase-100-plugin-compatible-fleet-layout.patch.md` | Refactor the fleet into a single-workspace plugin-compatible layout and validate both local plugin-dir loading and local marketplace install | The governed fleet works through `agents/` plus plugin metadata without a duplicate project |
| P11 | `phase-110-separate-repo-cutover.md` | `../design/design.md` plus package-local marketplace cutover posture | none | Prepare authority migration from the shared workspace into a standalone `general-expert` repo | Package can cut over to its own repo without duplicate authority |

---

## Overview flow diagram

```text
Initial state
  → agent files copied into governed source workspace
  → runtime copies still live in <user-runtime-agents>/
  → routing assumptions stronger than evidence

Current governed state
  → governed source workspace is authority for the managed fleet
  → per-agent design/changelog files exist
  → source agent files can be loaded from `agents/` through `--plugin-dir`
  → source agent files have also been synced into <user-runtime-agents>/
  → first routing validation matrix has completed
  → backend specialist policy is explicit for this environment
  → patch layer now captures sync / validation / reconciliation evidence
  → runtime-overlay interpretation is documented explicitly
```

---

## Review summary table

| Phase | Phase File | Sign-Off Status | Reviewer Severity | Reviewer Disposition | Blocker / Follow-Up State |
|------|------------|-----------------|-------------------|----------------------|---------------------------|
| P1 | `phase-010-governance-baseline.md` | Approved | None | Approved As-Is | master governance skeleton exists |
| P2 | `phase-020-per-agent-design-baseline.md` | Approved | None | Approved As-Is | per-agent design skeletons created |
| P3 | `phase-030-per-agent-changelog-baseline.md` | Approved | None | Approved As-Is | per-agent changelog skeletons created |
| P4 | `phase-040-runtime-sync.md` | Approved | None | Approved As-Is | source agents synced to runtime and deployed copies verified |
| P5 | `phase-050-validation.md` | Approved With Follow-up | Follow-Up | May Proceed With Follow-Up | first validation matrix completed; backend policy locked; broader frontend/runtime closure moved forward |
| P6 | `phase-060-governance-reconciliation.md` | Implemented - Pending Review | Review Pending | Awaiting Review | README/patch/status reconciliation added |
| P7 | `phase-070-runtime-overlay-governance.md` | Implemented - Pending Review | Review Pending | Awaiting Review | mixed-runtime interpretation documented |
| P8 | `phase-080-routing-policy-closure.md` | Implemented - Pending Review | Review Pending | Awaiting Review | Bun/browser/React operator policy baseline documented |
| P9 | `phase-090-multilingual-routing-interpretation.md` | In Progress | Review Pending | Awaiting Review | multilingual routing interpretation wave opened |
| P10 | `phase-100-plugin-compatible-fleet-layout.md` | Implemented - Pending Review | Review Pending | Awaiting Review | plugin-compatible fleet layout plus local marketplace install validated |

---

## Cross-phase coordination

- P1 established the source-of-truth model and the initial governance companion files.
- P2 established per-agent design authority across the full fleet.
- P3 established per-agent changelog authority across the full fleet.
- P4 completed the first governed source-to-runtime sync and verified the deployed copies.
- P5 completed the first validation matrix and identified follow-up refinement targets.
- The clearest explicit specialist wins in the first matrix were `nodejs-expert`, `bun-backend-expert`, and direct React hydration debugging via `react-frontend-expert`.
- The clearest follow-up gaps remained `nodejs-backend-expert` and `python-backend-expert` for architecture/implementation-heavy prompts.
- Two wording-tuning rounds were applied to both backend specialists.
- Revalidation still did not produce explicit specialist delegation for these heavy planning prompts.
- Current evidence supports treating architecture-heavy Node/FastAPI prompts as explicit-invocation-oriented specialist territory rather than continuing description-only tuning.
- Browser UI and Bun-runtime prompts stayed domain-aligned but did not always invoke specialists explicitly.
- P6 added the missing README and patch evidence layer and reconciled phase-state drift.
- P7 documented that routing evidence is gathered in a mixed live runtime that also contains unmanaged co-resident agents.
- P8 converted the remaining Bun/browser/React decision surface into explicit operator policy instead of leaving it implicit in TODO.
- P9 opens a bounded multilingual-routing interpretation wave so specialist descriptions rely more on task/domain intent than exact wording or prompt language.
- P10 refactored the fleet into a plugin-compatible `agents/` layout, validated local `--plugin-dir` loading, validated local marketplace install, and retired the redundant loose-file runtime copies in `<user-runtime-agents>/`.
- Changelog should record shipped or synchronized changes only.
- TODO should track execution work only.

---

## Verification requirements

End-to-end success should show:
- `general-expert/` remains the documented source-of-truth workspace
- `general-expert/agents/` remains the plugin-compatible runtime source for the managed fleet
- `<user-runtime-agents>/` remains the deployed runtime target when the deployed-copy path is still used
- master and per-agent design/changelog files remain aligned
- source and runtime agent files can be kept in sync intentionally
- the initial runtime sync and validation evidence is captured in patch form
- routing/debug work can be performed against the per-agent design targets with explicit policy guidance
- runtime-overlay interpretation remains honest about co-resident unmanaged agents
- design/changelog/TODO/phase/patch documents remain aligned with the active fleet model

---

## Rollback boundary

If the governance rollout becomes confusing or unstable:
- keep the current runtime agent files usable in `<user-runtime-agents>/`
- avoid deleting working runtime agents during documentation refactoring
- preserve the last known-good governed source wording before additional routing-policy changes
- prefer explicit patch-backed reconciliation over silent drift between artifact layers
