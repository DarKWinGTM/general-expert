# Bun Expert Design

> **Current Version:** 0.2.0
> **Last Updated:** 2026-03-30
> **Status:** Active - Policy Clarified
> **Full history:** [../changelog/bun-expert.changelog.md](../changelog/bun-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/bun-expert.md`
> **Runtime Target:** `<user-runtime-agents>/bun-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `bun-expert`.

This agent should own Bun runtime/tooling/platform expertise, not Bun-native backend architecture.

---

## 2. Ownership Boundary

### 2.1 Owns

- Bun runtime behavior
- Bun package manager / build / test / workflow issues
- Bun-vs-Node compatibility and migration questions
- Bun platform/toolchain behavior in local, CI, and deployment environments

### 2.2 Defers

- Bun-native backend APIs and services -> `bun-backend-expert`
- generic Node runtime/platform work -> `nodejs-expert`
- frontend concerns -> frontend expert agents

### 2.3 Not for

- Bun backend architecture when the real issue is service design
- generic package suggestions without Bun compatibility checks
- treating Bun as equivalent to Node without verification

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- bun install / bun build / bun test
- runtime/tooling/platform compatibility
- migration from Node to Bun
- Bun CI or workflow behavior

### 3.2 Common trigger examples

- why does `bun test` behave differently in CI?
- is this package compatible with Bun?
- should we migrate this Node toolchain to Bun?

### 3.3 Common misroute risks

- Bun backend prompts routing here instead of `bun-backend-expert`
- generic Node tooling prompts routing here instead of `nodejs-expert`

---

## 4. Prompt Structure Contract

Preferred body sections in the runtime agent file:
- `## Owns`
- `## Defers`
- `## Not for`
- `## Core Principles`
- `## Workflow`
- `## Verification Requirements`
- `## Output`

---

## 5. Validation Targets

The agent is working as intended when:
- Bun runtime/tooling prompts route here first or remain clearly Bun-runtime/tooling-aligned when handled by the main assistant
- Bun backend architecture prompts do not route here by default
- the agent clearly hands off Bun backend service design to `bun-backend-expert`

### 5.1 Current validation signal

Current workspace evidence shows:
- Bun backend architecture produced a clearer explicit specialist win for `bun-backend-expert`
- Bun runtime prompts stayed domain-aligned, but explicit specialist delegation was not always the observed path

### 5.2 Current operator policy

For this environment:
- Bun runtime prompts do **not** currently require additional routing tuning by default
- domain-aligned main-assistant handling is acceptable as long as the reasoning stays inside Bun runtime/tooling/platform scope
- explicit invocation remains available when specialist behavior is important

---

## 6. Planned Future Refinements

- refine `bun:test` / `bun build` / package-manager emphasis later only if real operator confusion persists
- revisit explicit-routing pressure later only if future validation shows material drift into the wrong specialist domain

---

> **Design anchor:** Bun platform/tooling first, Bun service architecture by deferral.