# Node.js Expert Design

> **Current Version:** 0.1.0
> **Last Updated:** 2026-03-28
> **Status:** Draft - Initial Skeleton
> **Full history:** [../changelog/nodejs-expert.changelog.md](../changelog/nodejs-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/nodejs-expert.md`
> **Runtime Target:** `<user-runtime-agents>/nodejs-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `nodejs-expert`.

This agent should remain the Node.js runtime / tooling / platform specialist, not a generic Node backend architecture agent.

---

## 2. Ownership Boundary

### 2.1 Owns

- Node runtime behavior
- event loop, streams, worker threads, diagnostics
- module resolution and ESM/CJS issues
- package/tooling/platform compatibility
- memory leaks, profiling, runtime debugging

### 2.2 Defers

- Node backend service architecture -> `nodejs-backend-expert`
- Bun runtime/tooling -> `bun-expert`
- frontend work -> frontend expert agents

### 2.3 Not for

- Express/Fastify/Nest service design unless the blocker is runtime/tooling-level
- auth/database/API architecture as the primary task
- frontend UI/component architecture

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- runtime/tooling/platform issues
- event loop / streams / ESM / compatibility / profiling language

### 3.2 Common trigger examples

- Node ESM/CJS resolution bugs
- stream backpressure or memory leak diagnosis
- runtime config or package compatibility failures
- profiling and performance investigation at runtime level

### 3.3 Common misroute risks

- backend API/auth/database prompts routing here instead of `nodejs-backend-expert`
- Bun-specific tooling prompts routing here instead of `bun-expert`

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
- runtime/tooling prompts route here first
- backend design prompts do not route here by default
- the agent explicitly hands off backend-design questions when appropriate

---

## 6. Planned Future Refinements

- tighten routing examples after real prompt-matrix validation
- refine wording if backend-vs-runtime collisions remain

---

> **Design anchor:** runtime/tooling/platform first, backend architecture second never.
