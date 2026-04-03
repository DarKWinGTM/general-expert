# Phase 100 - Plugin-compatible fleet layout

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P10
> **Status:** Implemented - Pending Review
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** [../patch/phase-100-plugin-compatible-fleet-layout.patch.md](../patch/phase-100-plugin-compatible-fleet-layout.patch.md)

---

## Objective

Refactor the `general-expert` fleet into a single-workspace plugin-compatible layout so the managed agents can be loaded from the same governed workspace through `--plugin-dir`.

## Why this phase exists

The old root-file layout governed the fleet well enough for loose-file sync into `~/.claude/agents/`, but it did not satisfy the standard plugin directory model. A plugin-compatible layout is needed if the same workspace is going to serve as the future local-plugin and distribution source.

## Action points / execution checklist

- [x] Add `.claude-plugin/plugin.json`
- [x] Create `agents/` and move the managed runtime files there
- [x] Fix runtime frontmatter parsing issues uncovered by plugin validation
- [x] Validate `claude --plugin-dir` visibility for the fleet
- [x] Complete full doc reconciliation for the new layout baseline needed for local marketplace install
- [x] Validate local marketplace install for the same governed fleet workspace
- [x] Validate `/reload-plugins` and restart-time visibility from the marketplace-installed path
- [x] Retire the redundant deployed-copy path in favor of marketplace-distributed activation for this fleet

## Verification

- plugin manifest validates
- the full fleet appears in `claude --plugin-dir ... agents`
- direct invocation works for checked fleet members
- no duplicate project was created

## Exit criteria

- the workspace works as a plugin-compatible source
- remaining governance reconciliation work is explicitly tracked
