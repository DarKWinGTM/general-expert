# Phase 040 - Runtime Sync

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P4
> **Status:** Completed
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** [../patch/phase-040-runtime-sync.patch.md](../patch/phase-040-runtime-sync.patch.md)

---

## Objective

Define and execute the standard synchronization path from governed source agent files in `general-expert/` to the active runtime deployment directory `<user-runtime-agents>/`.

## Why this phase exists

The governed source workspace only becomes operationally useful when there is a repeatable way to push its agent files into the runtime directory without creating drift.

## Design extraction

- Source design: `../design/design.md` section `Sync Workflow Baseline`
- Derived execution work: define the runtime sync discipline and apply it across the managed agents
- Target outcome: runtime copies stay intentionally aligned with the governed source files

## Entry conditions / prerequisites

- Governance baseline exists
- Per-agent design files exist
- Per-agent changelog files exist

## Action points / execution checklist

- [x] Decide the canonical sync procedure for source → runtime deployment
- [x] Apply the sync procedure for all managed source agent files
- [x] Verify that runtime copies exist in `<user-runtime-agents>/`
- [x] Verify that deployed copies reflect the intended governed source state
- [x] Record the sync event in changelog/TODO and patch evidence

## Out of scope

- Prompt-routing matrix execution
- Deep prompt-level routing refinement
- Support-document expansion

## Affected artifacts

- `../*.md` source agent files
- `<user-runtime-agents>/*.md`
- `../patch/phase-040-runtime-sync.patch.md`
- `../TODO.md`
- `../changelog/changelog.md`

## TODO coordination

This phase closed the initial runtime-sync discipline work and established the managed source-to-runtime parity baseline.

## Changelog coordination

The completed sync event is recorded in the master changelog as a synchronized runtime-alignment milestone.

## Evidence / Patch Outputs

- `../patch/phase-040-runtime-sync.patch.md` captures the before/after sync surface and the managed runtime-parity evidence.

## Verification

- Source and runtime copies both exist
- Runtime copies are discoverable by Claude Code
- No unexpected drift remains between the intended source version and the deployed runtime version for the 7 managed agents

## Exit criteria

- The sync procedure is explicit
- Runtime files are aligned with governed source files
- The before/after sync evidence is captured in patch form

## Risks / rollback notes

- Avoid editing runtime-only files without back-porting to source
- If sync introduces confusion, preserve the last known-good runtime copy and reconcile source carefully

## Next possible phases

- `phase-050-validation.md`
- `phase-060-governance-reconciliation.md`
