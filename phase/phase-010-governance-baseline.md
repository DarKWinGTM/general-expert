# Phase 010 - Governance Baseline

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P1
> **Status:** Completed
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** none

---

## Objective

Establish the governance baseline for the `general-expert` fleet so the workspace has a clear source-of-truth model before deeper rollout work begins.

## Why this phase exists

Without a baseline governance layer, later routing, sync, and validation work would drift between source files and runtime files.

## Design extraction

- Source design: `../design/design.md` sections `Source-of-Truth Model`, `Authoring Contract`, `Governance Companions`
- Derived execution work: create master governance documents and lock the source-vs-runtime authority model
- Target outcome: one governed workspace that clearly owns future agent changes

## Entry conditions / prerequisites

- The source agent files exist in `general-expert/`
- Runtime deployment target remains `~/.claude/agents/`

## Action points / execution checklist

- [x] Create `design/design.md`
- [x] Create `changelog/changelog.md`
- [x] Create `TODO.md`
- [x] Create `phase/SUMMARY.md`
- [x] Establish source-of-truth wording for `general-expert/` vs `~/.claude/agents/`

## Out of scope

- Per-agent design details
- Per-agent changelog files
- Runtime sync execution
- Prompt-routing validation

## Affected artifacts

- `../design/design.md`
- `../changelog/changelog.md`
- `../TODO.md`
- `SUMMARY.md`

## TODO coordination

This phase closes the initial governance-baseline setup items and unlocks the per-agent design/changelog work.

## Changelog coordination

This phase should be represented in the master changelog as the baseline governance initialization step.

## Verification

- Governance companion files exist
- Source-of-truth wording is explicit
- Summary file references the governed workspace correctly

## Exit criteria

- The governed workspace has its master design/changelog/TODO/phase documents
- Source-vs-runtime authority is explicit

## Risks / rollback notes

- Keep runtime agents untouched during governance setup
- Treat governance files as additive until runtime sync begins

## Next possible phases

- `phase-020-per-agent-design-baseline.md`
- `phase-030-per-agent-changelog-baseline.md`
