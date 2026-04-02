# Phase 100 Plugin-Compatible Fleet Layout Patch

## 0) Document Control

> **Current Version:** 1.1
> **Status:** Implemented - Pending Review
> **Target Design:** [../design/design.md](../design/design.md) v0.4.0
> **Target Phase:** [../phase/phase-100-plugin-compatible-fleet-layout.md](../phase/phase-100-plugin-compatible-fleet-layout.md)
> **Session:** dd0bf4af-a66b-4b07-bb9d-a90a0e57b54e
> **Full history:** [../changelog/changelog.md](../changelog/changelog.md)

---

## 1) Context

This patch captures the refactor of the `general-expert` fleet into a single-workspace plugin-compatible layout and its extension into a validated local marketplace install path.

## 2) Analysis

Risk level: Medium

The original workspace structure supported governed source control and loose-file sync into `<user-runtime-agents>/`, but it did not satisfy the standard plugin directory model. If the same governed fleet is going to be tested and evolved through `--plugin-dir`, the runtime files need to live under `agents/` and the workspace needs plugin metadata.

---

## 3) Change Items

### Change Item 1
- **Target location:** workspace runtime layout
- **Change type:** restructuring

**Before**
```text
general-expert/
  nodejs-expert.md
  nodejs-backend-expert.md
  bun-expert.md
  bun-backend-expert.md
  html-css-js-frontend-expert.md
  react-frontend-expert.md
  python-backend-expert.md
```

**After**
```text
general-expert/
  .claude-plugin/plugin.json
  agents/
    nodejs-expert.md
    nodejs-backend-expert.md
    bun-expert.md
    bun-backend-expert.md
    html-css-js-frontend-expert.md
    react-frontend-expert.md
    python-backend-expert.md
```

### Change Item 2
- **Target location:** runtime agent frontmatter
- **Change type:** replacement

**Before**
```text
Long description lines used unquoted YAML values, which caused plugin validation parse errors and dropped metadata at runtime.
```

**After**
```text
Long description lines are quoted so YAML frontmatter parses correctly during plugin validation and local plugin loading.
```

### Change Item 3
- **Target location:** fleet activation model
- **Change type:** additive

**Before**
```text
The workspace only described governed source files plus deployment to <user-runtime-agents>/.
```

**After**
```text
The workspace now also supports local plugin-compatible loading through `claude --plugin-dir <workspace-root>`.
```

### Change Item 4
- **Target location:** shared local marketplace root and local Claude settings persistence
- **Change type:** additive

**Before**
```text
No shared local marketplace manifest exposed `general-expert` for marketplace-style local install, and no local settings entry persisted this fleet as an installed plugin.
```

**After**
```text
A shared marketplace manifest at `<marketplace-root>/.claude-plugin/marketplace.json` exposes `general-expert`, local marketplace declaration persists through `.claude/settings.local.json`, local install materializes a cached plugin copy at `~/.claude/plugins/cache/darkwingtm/general-expert/1.0.0/`, and the redundant loose-file copies under `<user-runtime-agents>/` are removed.
```

---

## 4) Verification

- [x] `.claude-plugin/plugin.json` exists
- [x] managed runtime files now live under `agents/`
- [x] plugin validation passes
- [x] `claude --plugin-dir ... agents` shows the `general-expert:*` fleet
- [x] direct invocation works in the checked plugin-dir session
- [x] shared local marketplace manifest validates
- [x] `claude plugins marketplace add <marketplace-root> --scope local` succeeds
- [x] `claude plugins install general-expert@darkwingtm --scope local` succeeds
- [x] `claude agents` shows the `general-expert:*` fleet after local marketplace install
- [x] `claude agents` still shows the `general-expert:*` fleet after `/reload-plugins`

---

## 5) Rollback Approach

If this direction proves wrong, keep one governed workspace and revert the runtime layout there rather than creating a duplicate plugin project. The rollback-safe principle is single-workspace authority, not parallel package copies.
