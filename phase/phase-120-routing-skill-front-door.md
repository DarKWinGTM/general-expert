# Phase 120 - Routing skill front door

> **Summary File:** [SUMMARY.md](SUMMARY.md)
> **Phase ID:** P12
> **Status:** Implemented - Pending Review
> **Design References:** [../design/design.md](../design/design.md)
> **Patch References:** [../patch/phase-120-routing-skill-front-door.patch.md](../patch/phase-120-routing-skill-front-door.patch.md)

---

## Objective

Add an operator-facing routing skill so users can choose the right `general-expert` specialist and understand explicit-invocation guidance without depending only on agent-name recall.

## Why this phase exists

The fleet already had stronger routing metadata, bounded multilingual guidance, and explicit-invocation policy notes for backend specialists. What it still lacked was a practical front door. Without a routing skill, users had to remember specialist names and boundaries directly. This phase closes that usability gap while keeping runtime authority in the managed agent files.

## Entry conditions / prerequisites

- the 7-agent fleet already exists under `../agents/`
- multilingual intent-oriented routing wording is already applied
- explicit-invocation policy for `nodejs-backend-expert` and `python-backend-expert` is already documented
- repo-root local marketplace install and restart-time visibility are already validated

## Action points / execution checklist

- [x] create `../skills/routing/SKILL.md`
- [x] define a compact routing map across runtime, backend, frontend, and browser-platform boundaries
- [x] explain when explicit invocation is safer than relying on auto-routing
- [x] keep the skill bounded as a support-facing front door rather than a competing runtime authority
- [x] sync README/design/changelog/TODO/phase wording for the new operator surface
- [x] bump plugin and marketplace package versions to `1.2.0`

## Out of scope

- rewriting the managed agent bodies beyond already-approved routing metadata work
- replacing the existing agent files as the main runtime authority
- claiming stronger auto-routing guarantees than the checked validation evidence supports
- introducing a second routing authority outside the governed package

## Affected artifacts

- `../skills/routing/SKILL.md`
- `../README.md`
- `../design/design.md`
- `../changelog/changelog.md`
- `../TODO.md`
- `../phase/SUMMARY.md`
- `../patch/phase-120-routing-skill-front-door.patch.md`
- `../.claude-plugin/plugin.json`
- `../.claude-plugin/marketplace.json`

## TODO coordination

This phase converts the routing front door from an implicit future idea into shipped operator-facing package behavior.

## Changelog coordination

Record the routing skill only after the skill file, package metadata, and fleet-level governance docs are aligned.

## Verification

Success should mean:
- `skills/routing/SKILL.md` exists and gives a usable specialist-selection front door
- the routing map explains backend vs runtime vs React vs browser-platform boundaries clearly
- explicit-invocation guidance remains visible for the backend specialists that still need it most
- README/design/TODO/phase all describe the routing skill as support-facing rather than as competing runtime authority
- plugin and marketplace metadata expose version `1.2.0`

## Exit criteria

- the routing skill file exists
- fleet-level governance docs are synced
- package versions are bumped consistently
- the new front door improves operator usability without overclaiming routing certainty

## Risks / rollback notes

- do not let the routing skill drift into a second authority that competes with `agents/*.md`
- do not overstate routing confidence beyond the checked validation evidence
- if the routing map creates new ambiguity, narrow the guidance instead of broadening every specialist boundary

## Next possible phases

- a routing-debug support sheet under `support/`
- a follow-up validation slice if live routing evidence shows recurring boundary confusion despite the new front door
