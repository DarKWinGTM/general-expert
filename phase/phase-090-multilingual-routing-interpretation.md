# Phase 090 - Multilingual routing interpretation

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P9
> **Status:** In Progress
> **Design References:** [../design/design.md](../design/design.md), [../design/nodejs-expert.design.md](../design/nodejs-expert.design.md), [../design/nodejs-backend-expert.design.md](../design/nodejs-backend-expert.design.md), [../design/bun-expert.design.md](../design/bun-expert.design.md), [../design/bun-backend-expert.design.md](../design/bun-backend-expert.design.md), [../design/html-css-js-frontend-expert.design.md](../design/html-css-js-frontend-expert.design.md), [../design/react-frontend-expert.design.md](../design/react-frontend-expert.design.md), [../design/python-backend-expert.design.md](../design/python-backend-expert.design.md)
> **Patch References:** [../patch/phase-090-multilingual-routing-interpretation.patch.md](../patch/phase-090-multilingual-routing-interpretation.patch.md)

---

## Objective

Improve multilingual prompt interpretation for the specialist fleet without translating full agent bodies into other languages.

## Why this phase exists

Current routing metadata is still primarily English-only. Official docs do not explicitly prove that Thai prompts route worse than English, but they do clearly say that `description` wording and user phrasing matter for automatic selection. The cleanest evidence-backed improvement is therefore to make routing metadata more intent-oriented and language-agnostic rather than hard-coding one language through alias lists.

## Entry conditions / prerequisites

- Source-governed fleet baseline already exists
- Runtime sync and validation waves already completed
- Explicit invocation policy for Node/Python backend specialists is already locked
- Bun/browser/React operator-policy baseline is already documented

## Action points / execution checklist

- [x] Add the multilingual-routing wave to `TODO.md`
- [x] Add P9 to `phase/SUMMARY.md`
- [ ] Update fleet-level design and README to define multilingual routing at the `description` layer only
- [ ] Update all 7 source runtime agent `description` lines to emphasize intent-based routing rather than exact wording or prompt language
- [ ] Update per-agent design files with multilingual routing guidance
- [x] Record the before/after surface in patch form
- [ ] Update master and per-agent changelogs after implementation is complete
- [ ] Sync changed source agents into `~/.claude/agents/`
- [ ] Run a small multilingual prompt matrix and record remaining collisions explicitly

## Out of scope

- Full translation of runtime agent bodies
- New agent creation
- Central RULES changes
- Replacing the already-locked explicit-invocation policy for Node/Python backend specialists

## Affected artifacts

- `../README.md`
- `../design/design.md`
- `../TODO.md`
- `../phase/SUMMARY.md`
- `../patch/phase-090-multilingual-routing-interpretation.patch.md`
- all 7 runtime agent files at the workspace root
- all 7 per-agent design files
- master and per-agent changelog files
- deployed managed runtime copies under `~/.claude/agents/`

## TODO coordination

This phase should convert multilingual-routing support from an implicit concern into explicit execution work with a bounded validation target.

## Changelog coordination

Do not write completion history until the routing wording changes are actually implemented and synced.

## Verification

Success should mean:
- source agent descriptions now emphasize intent-based routing rather than exact wording or prompt language
- agent bodies remain English
- multilingual prompts land closer to the intended specialist domain without major new collisions
- explicit-invocation policy for Node/Python backend specialists remains intact
- Bun/browser/React domains become easier to match across languages without forcing a body rewrite

## Exit criteria

- P9 artifacts are in place
- multilingual routing wording exists in all intended source agent descriptions
- design and README explain the policy cleanly
- patch captures the before/after surface
- sync to `~/.claude/agents/` is complete
- validation notes are recorded honestly

## Risks / rollback notes

- Do not bloat descriptions until they become noisy or truncated
- Do not replace intent-based wording with hard-coded language-specific alias lists
- If a wording change causes a collision, remove or narrow it rather than broadening adjacent agents further

## Next possible phases

- a narrower follow-up validation slice if multilingual prompts still misroute materially after wording cleanup
