# Phase 090 Multilingual Routing Interpretation Patch

## 0) Document Control

> **Current Version:** 1.0
> **Status:** In Progress
> **Target Design:** [../design/design.md](../design/design.md) v0.2.0
> **Target Phase:** [../phase/phase-090-multilingual-routing-interpretation.md](../phase/phase-090-multilingual-routing-interpretation.md)
> **Session:** 599bf14e-665e-4915-a64a-535b73bed417
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch exists to capture the before/after routing surface for improving multilingual routing interpretation across the specialist fleet.

Why this change matters:
- current runtime descriptions are mostly English-only
- official docs clearly say `description` wording and user phrasing matter for routing
- the user wants stronger multilingual interpretation without rewriting full agent bodies into other languages

---

## 2) Analysis

Risk level: Medium

Dependencies:
- `../design/design.md`
- all 7 per-agent design files
- all 7 source runtime agent files
- `../README.md`
- `../TODO.md`
- `../phase/SUMMARY.md`

Review concern:
- routing wording must improve cross-language intent matching without collapsing into keyword-list hard matching or creating major cross-agent collisions

---

## 3) Change Items

### Change Item 1
- **Target location:** all 7 source runtime agent `description` lines
- **Change type:** replacement

**Before**
```text
English-only routing metadata or mostly English routing metadata.
```

**After**
```text
Descriptions stay English, but explicitly say that routing should follow task intent rather than exact wording or prompt language.
```

### Change Item 2
- **Target location:** fleet-level and per-agent routing policy docs
- **Change type:** additive

**Before**
```text
Routing intent explains English trigger examples but does not define a multilingual interpretation policy.
```

**After**
```text
Routing intent explicitly says multilingual prompt support should rely on intent-oriented routing language rather than language-specific alias lists, while substantive bodies remain English.
```

### Change Item 3
- **Target location:** multilingual validation surface
- **Change type:** additive

**Before**
```text
No explicit multilingual prompt matrix exists for the specialist fleet.
```

**After**
```text
A small multilingual prompt matrix is used to check whether specialist prompts align more closely with the intended domains without introducing new collisions.
```

---

## 4) Verification

- [ ] Confirm all 7 source agent descriptions now emphasize intent-based routing instead of exact wording or prompt language
- [ ] Confirm runtime bodies remain English
- [ ] Confirm fleet-level design and per-agent design files now define multilingual interpretation policy clearly
- [ ] Confirm the patch shows before/after description examples for the changed agents
- [ ] Confirm a small multilingual prompt matrix is recorded and interpreted honestly

---

## 5) Rollback Approach

If the new routing wording causes confusion or new collisions:
- narrow the wording for the affected agent
- keep the English description baseline intact
- preserve the patch as the historical record of the attempted multilingual-routing refinement
