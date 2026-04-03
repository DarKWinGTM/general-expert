# General Expert Agents - TODO

> **Last Updated:** 2026-04-03

---

## ✅ Completed

- [x] Established `general-expert/` as governed source workspace for the expert-agent fleet.
- [x] Copied current agent source files into `general-expert/` for easier design/changelog/TODO/phase development.
- [x] Created governance skeleton files for design, changelog, TODO, and phase summary.
- [x] Created per-agent `design/*.design.md` skeleton files for all 7 managed agents.
- [x] Created per-agent `changelog/*.changelog.md` skeleton files for all 7 managed agents.
- [x] Completed phase-child-file baseline for P1-P5.
- [x] Synced the 7 governed source agent files into `<user-runtime-agents>/` and verified deployed copies match source.
- [x] Executed the first routing-validation wave and recorded backend specialist policy evidence.
- [x] Added `README.md` and the initial `patch/*.patch.md` evidence layer.
- [x] Reconciled phase/state drift across design, changelog, TODO, and phase artifacts.
- [x] Opened the 060/070/080 governance-hardening family.
- [x] Documented runtime-overlay interpretation and frontend/runtime routing-policy closure rules.
- [x] Refactored the fleet into `agents/` plus `.claude-plugin/plugin.json` and verified local `--plugin-dir` loading without creating a duplicate project.

---

## 📋 Tasks To Do

### Current Governance Execution
- [x] Review the 060/070/080 governance-hardening wave across README/design/changelog/TODO/phase/patch for consistency.
- [x] Execute the multilingual-routing interpretation wave so specialist descriptions rely more on task/domain intent than exact wording or prompt language, without translating full agent bodies.
- [x] Validate that local marketplace install can replace plugin-dir for stable local activation of the governed fleet.
- [x] Validate `/reload-plugins` visibility from the marketplace-installed path.
- [x] Validate restart-time visibility from the marketplace-installed path.
- [x] Retire the redundant loose-file runtime copies from `<user-runtime-agents>/` in favor of the marketplace-installed path for this fleet.
- [ ] Complete separate-repo cutover and retire shared-workspace authority once the standalone repo becomes the source of truth.

### Deferred Enhancements
- [ ] Add `support/routing-debug-sheet.md` for reusable routing diagnostics.
- [ ] Add `support/sync-checklist.md` for repeatable deployment hygiene.
- [ ] Add phased rollout files later if the fleet evolves through another bounded implementation slice beyond the current reconciliation wave.

---

## 📜 History

| Date | Changes |
|------|---------|
| 2026-04-03 | Applied multilingual intent-oriented routing metadata across the 7 agent descriptions, synced the fleet-level docs/governance wording, and bumped the plugin/marketplace package versions to `1.1.0`. |
| 2026-04-03 | Normalized public install docs to the standalone repo root, validated `claude plugins marketplace add ./ --scope local` plus `claude plugins install general-expert@general-expert --scope local` from the repo root in an isolated HOME, and kept the shared `darkwingtm` path scoped as checked local workspace-development context. |
| 2026-04-02 | Added the shared local marketplace scaffold, validated local-scope plugin install for `general-expert`, recorded the persisted local settings entry plus plugin-cache path model, and resynchronized README/design/changelog/TODO/phase/patch to match the new activation truth. |
| 2026-03-30 | Added workspace `README.md`, created the initial `patch/*.patch.md` evidence layer, reconciled P4/P5 phase status drift, opened phases 060/070/080, documented runtime-overlay interpretation, and closed the current frontend/runtime routing-policy decision surface. |
| 2026-03-28 | Completed narrow backend validation matrix v2. Results: `nodejs-backend-expert` = FAIL(explicit)/PASS(domain) for N2-v2 and N4-v2, INCONCLUSIVE for N1-v2 due missing Fastify target in scope; `python-backend-expert` = FAIL(explicit)/PASS(domain) for P2-v2 and P5-v2, INCONCLUSIVE for P1-v2 due missing FastAPI OAuth callback target in scope. |
| 2026-03-28 | Classified narrow backend validation round one: architecture/implementation-heavy prompts for `nodejs-backend-expert` and `python-backend-expert` remained FAIL for explicit routing, while several narrow prompts were marked INCONCLUSIVE because they referenced missing or ambiguous target artifacts in the checked scope. |
| 2026-03-28 | Defined narrow backend validation matrix v2 with self-contained prompts for `nodejs-backend-expert` and `python-backend-expert`. |
| 2026-03-28 | Completed a second description-tightening round for `nodejs-backend-expert` and `python-backend-expert`. Revalidation still did not produce explicit specialist routing: the Node backend architecture prompt fell back to generic architecture handling, and the FastAPI implementation prompt remained in generic plan-mode flow. |
| 2026-03-28 | Completed the first routing validation matrix: explicit PASS for `nodejs-expert`, `bun-backend-expert`, and direct React hydration debugging via `react-frontend-expert`; `nodejs-backend-expert` backend-architecture prompt still did not route explicitly; `python-backend-expert` FastAPI implementation prompt was intercepted by generic plan-mode workflow; browser UI and Bun-runtime prompts remained domain-aligned but did not always invoke specialists explicitly. |
| 2026-03-28 | Completed runtime sync for the 7 governed source agents into `<user-runtime-agents>/` and verified deployed copies match source. |
| 2026-03-28 | Added per-agent `design/*.design.md` and `changelog/*.changelog.md` skeleton files for all 7 managed agents. |
| 2026-03-28 | Created the governance baseline for `general-expert/`: initialized `design/design.md`, `changelog/changelog.md`, `TODO.md`, and `phase/SUMMARY.md` skeleton files. |
| 2026-03-28 | Moved the main expert-agent source files into `<workspace-root>/` to support governed design/changelog/TODO/phase development. |
