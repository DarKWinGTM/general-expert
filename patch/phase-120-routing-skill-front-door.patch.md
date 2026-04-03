# Phase 120 Routing Skill Front Door Patch

## 0) Document Control

> **Current Version:** 1.0
> **Status:** Implemented - Pending Review
> **Target Design:** [../design/design.md](../design/design.md) v0.6.0
> **Target Phase:** [../phase/phase-120-routing-skill-front-door.md](../phase/phase-120-routing-skill-front-door.md)
> **Session:** dd0bf4af-a66b-4b07-bb9d-a90a0e57b54e
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch captures the before/after change surface for adding a dedicated routing-skill front door to the `general-expert` fleet.

## 2) Analysis

Risk level: Low to Medium

The fleet already had specialist runtime files and bounded routing-policy evidence, but operator usage still depended heavily on memorizing agent names. A routing skill is the smallest product-facing addition that improves discoverability and explicit-invocation guidance without changing the actual runtime ownership model.

---

## 3) Change Items

### Change Item 1
- **Target location:** `skills/routing/SKILL.md`
- **Change type:** additive

**Before**
```text
No dedicated routing skill exists. Users must infer specialist boundaries directly from agent names and runtime descriptions.
```

**After**
```text
A routing skill exists with a compact routing map, explicit-invocation guidance, multilingual intent notes, and bounded output expectations for specialist selection.
```

### Change Item 2
- **Target location:** fleet-level docs and governance surfaces
- **Change type:** additive

**Before**
```text
README/design/TODO/phase describe multilingual routing posture and package authority, but they do not yet expose a concrete operator-facing front door for specialist selection.
```

**After**
```text
README/design/TODO/phase now describe the routing skill as a support-facing front door that improves package usability without competing with the managed agent files as runtime authority.
```

### Change Item 3
- **Target location:** package metadata
- **Change type:** replacement

**Before**
```text
Plugin and marketplace metadata still expose the pre-routing-skill package version.
```

**After**
```text
Plugin and marketplace metadata are bumped to `1.2.0` so installed update flow can surface the new routing front door.
```

---

## 4) Verification

- [x] `skills/routing/SKILL.md` exists
- [x] the routing skill includes a compact specialist-selection map
- [x] explicit-invocation guidance remains visible for backend specialist boundaries
- [x] README/design/TODO/phase all describe the routing skill as support-facing
- [x] plugin and marketplace metadata expose version `1.2.0`

---

## 5) Rollback Approach

If the routing skill proves confusing or starts competing with the runtime authority model, keep the existing agent files authoritative, remove or narrow the routing skill guidance, and preserve this patch as the record of the attempted front-door improvement.
