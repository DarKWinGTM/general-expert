---
name: General Expert Routing Skill
description: Use this skill to choose the right general-expert specialist, understand when explicit invocation is recommended, and route backend/frontend/runtime questions to the best-fit expert more reliably.
version: 1.0.0
---

# General Expert Routing Skill

This skill is the active front-door support surface for the governed `general-expert` fleet.

## What this skill is for
Use it when you need to:
- choose the right specialist from the fleet
- understand backend vs runtime vs frontend boundaries
- decide when explicit invocation matters more than relying on auto-routing
- map multilingual prompts into the intended specialist domain

## Quick routing map

| Situation | Best Fit | Why |
|---|---|---|
| Node runtime/tooling/platform issue | `nodejs-expert` | Owns Node runtime and tooling behavior |
| Node backend/API/service issue | `nodejs-backend-expert` | Owns Node backend architecture and operations |
| Bun runtime/tooling issue | `bun-expert` | Owns Bun runtime and tooling behavior |
| Bun-native backend/API issue | `bun-backend-expert` | Owns Bun-native backend architecture |
| Semantic HTML/CSS/browser-platform issue | `html-css-js-frontend-expert` | Owns browser-platform and vanilla frontend work |
| React/Next/Vite framework issue | `react-frontend-expert` | Owns React/framework frontend work |
| Python backend/API issue | `python-backend-expert` | Owns Python backend services and APIs |

## Explicit invocation guidance

Prefer explicit invocation when:
- you need `nodejs-backend-expert` for architecture-heavy backend work
- you need `python-backend-expert` for architecture-heavy backend work
- you want to remove ambiguity between React and browser-platform surfaces
- you are testing routing quality itself rather than just needing a good answer

## Multilingual routing guidance

The fleet now uses intent-oriented routing metadata rather than exact wording or prompt language.

Practical meaning:
- Thai/English mixed prompts should still map by domain intent
- backend/API/service intent should beat generic runtime wording when the service context is clear
- React/framework intent should beat browser-platform routing when the app/framework context is explicit
- browser-platform routing should win when the issue is really semantic HTML, CSS, DOM, or browser behavior rather than framework architecture

## Output expectations
- best-fit specialist recommendation
- short reason why that specialist fits
- explicit note when explicit invocation is safer than auto-routing
- one fallback alternative only if the boundary is genuinely close
