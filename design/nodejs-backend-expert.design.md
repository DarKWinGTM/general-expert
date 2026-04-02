# Node.js Backend Expert Design

> **Current Version:** 0.2.0
> **Last Updated:** 2026-03-28
> **Status:** Draft - Validation Follow-up Active
> **Full history:** [../changelog/nodejs-backend-expert.changelog.md](../changelog/nodejs-backend-expert.changelog.md)

---

## 0. Document Control

> **Parent Scope:** General Expert Agents
> **Design Type:** Per-Agent Design
> **Runtime File:** `../agents/nodejs-backend-expert.md`
> **Runtime Target:** `<user-runtime-agents>/nodejs-backend-expert.md`

---

## 1. Purpose

Define the intended behavior, routing boundary, and runtime role of `nodejs-backend-expert`.

This agent should own Node.js backend application and API architecture, clearly separated from low-level Node runtime/tooling expertise.

---

## 2. Ownership Boundary

### 2.1 Owns

- Node backend services and APIs
- Express / Fastify / Nest / Koa / Hono-on-Node
- auth, middleware, DB integration, caching, queues
- backend deployment and operational concerns for Node services

### 2.2 Defers

- low-level runtime/tooling internals -> `nodejs-expert`
- Bun-native backend architecture -> `bun-backend-expert`
- frontend concerns -> frontend expert agents

### 2.3 Not for

- pure module-resolution/profiling/runtime diagnosis
- browser/frontend architecture
- generic package/tooling compatibility work without backend context

---

## 3. Routing Intent

### 3.1 Description intent

The `description` line should route prompts involving:
- backend APIs
- auth flows
- database/service design
- middleware, queues, caching, backend scaling

### 3.2 Common trigger examples

- build a Fastify API with JWT auth and Postgres
- review NestJS service architecture
- add Redis caching and background jobs to a Node backend
- ออกแบบ backend Node + API + auth + database
- review ระบบหลังบ้าน Node / Express / Fastify
- แก้ middleware, auth, queue, หรือ worker ของ backend Node

### 3.2A Multilingual routing rule

Multilingual prompt support should live in the runtime file `description` line through intent-oriented routing language rather than hard-coded language-specific alias lists.
The body should remain English.

### 3.3 Common misroute risks

- runtime/tooling prompts routing here instead of `nodejs-expert`
- Bun backend prompts routing here instead of `bun-backend-expert`

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
- backend/API architecture prompts route here first
- low-level Node runtime prompts do not route here by default
- the agent explicitly defers to `nodejs-expert` for runtime/tooling blockers

### 5.1 Current validation result

First validation matrix status:
- backend architecture/design prompt did **not** trigger `nodejs-backend-expert` explicitly
- this is the clearest current routing gap in the fleet

### 5.2 Planned correction target

Primary correction target:
- strengthen the runtime file description line so prompts containing Fastify/API/JWT/PostgreSQL/Redis/background-jobs/backend-architecture language route here more reliably

### 5.3 Correction applied

Applied in the governed source/runtime files:
- expanded line-3 routing language to emphasize backend architecture and API implementation prompts explicitly
- added stronger directive wording: "Use this agent specifically" and "Prefer this agent when the user asks how to build, structure, or review a Node backend"

### 5.4 Second validation result

Second validation matrix status:
- the backend architecture/design prompt still did **not** explicitly trigger `nodejs-backend-expert`
- in the second rerun, the prompt was handled directly by the main assistant with docs-lookup attempts rather than explicit specialist delegation
- current conclusion: line-3 tightening alone is still insufficient to force explicit specialist routing for this architecture-heavy prompt class

### 5.5 Narrow validation matrix v2 result

Round-two classification for `nodejs-backend-expert`:
- **FAIL (explicit routing):** N2-v2 and N4-v2 remained main-assistant direct handling instead of explicit specialist delegation
- **PASS (domain alignment only):** N2-v2 and N4-v2 still stayed inside Node backend auth/worker/idempotency reasoning rather than drifting to runtime/frontend specialists
- **INCONCLUSIVE:** N1-v2 assumed a Fastify auth middleware artifact that was not present in the checked workspace, so it remained a target-existence mismatch rather than a clean routing test

### 5.6 Current conclusion

For this environment, `nodejs-backend-expert` is currently better understood as a governed specialist definition that may still require explicit invocation or attached target files for reliable use. The main assistant often handles backend review/debug prompts directly even when the prompt is self-contained.

---

## 6. Usage Guidance

### 6.1 Best current usage model

For this environment, `nodejs-backend-expert` performs best when used as an **explicit-invocation-oriented specialist** rather than a delegation-first auto-routed specialist.

### 6.2 Preferred prompting shape

Use this agent most intentionally when:
- you explicitly invoke `nodejs-backend-expert`
- you attach concrete file paths or pasted backend code/design snippets
- the task is framed as **review**, **debug**, or **refactor** rather than broad architecture planning

Avoid assuming that broad natural-language planning prompts will auto-route here reliably.

### 6.3 Copy-paste prompt templates

#### Template 1 — auth review
```text
Use nodejs-backend-expert to review this Node backend auth/token flow.

Target files:
- /path/file1
- /path/file2

Focus on:
- refresh rotation
- replay risk
- cookie/session persistence
- logout invalidation
```

#### Template 2 — middleware review
```text
Use nodejs-backend-expert to review this backend middleware flow.

Target files:
- /path/auth-middleware.ts
- /path/routes.ts

Focus on:
- JWT verification
- route protection
- middleware ordering
- error handling
```

#### Template 3 — queue/idempotency review
```text
Use nodejs-backend-expert to review this Node backend worker/queue integration.

Target files:
- /path/worker.ts
- /path/queue.ts

Focus on:
- retry policy
- idempotency
- duplicate processing
- atomic completion
```

#### Template 4 — backend refactor
```text
Use nodejs-backend-expert to refactor this Node backend service boundary.

Target files:
- /path/controller.ts
- /path/service.ts
- /path/repo.ts

Focus on:
- transport vs business logic separation
- transaction boundary
- cache invalidation
```

#### Template 5 — focused debug
```text
Use nodejs-backend-expert to debug this Node backend issue.

Target files:
- /path/file1
- /path/file2

Focus on:
- exact failure mode
- likely root cause
- minimal safe fix
- regression risk
```

## 7. Planned Future Refinements

- refine framework emphasis if Fastify vs NestJS routing needs sharper wording
- replace ambiguous narrow-matrix prompts with self-contained review/debug prompts for explicit-routing validation

## 8. Narrow Backend Validation Matrix v2

### Node.js backend-focused prompts

- **N1-v2**
  - `Review a Fastify auth middleware design for security and correctness. Focus on JWT verification, request decoration, route protection, error handling, and token/session edge cases.`
- **N2-v2**
  - `Debug an Express JWT refresh-token flow where tokens rotate incorrectly after login. Focus on refresh token issuance, rotation, invalidation, replay protection, cookie/token persistence, and post-login session consistency.`
- **N4-v2**
  - `Review a Node backend worker integration for retry and idempotency issues. Focus on Redis-backed queues, job retries, duplicate processing, atomic completion, and webhook/payment race conditions.`

### Success criterion

These prompts should be self-contained enough to test backend-specialist routing directly without requiring missing design files or missing queue/framework artifacts in the workspace.

---

> **Design anchor:** service/API/backend first, runtime internals by deferral.
