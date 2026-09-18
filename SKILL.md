---
name: taste-loop
description: Discover a product's visual direction and refine its rendered interface through explicit taste decisions, implementation, and screenshot critique. Use when the user invokes Taste Loop, wants help finding their taste, asks to compare distinct design directions, or requests iterative visual refinement. Handle narrow fixes and fully specified designs through normal implementation instead.
license: MIT
compatibility: Requires project file access and a way to run the product. Web research, vision, screenshots, browser or simulator control, image generation, video generation, and subagents improve the result but are optional.
metadata:
  author: AbdulsaboorS
  version: "0.1.0"
---

# Taste Loop

Resolve the user's taste, build one coherent direction, and judge rendered evidence until they accept it.

## Authority And Boundaries

- The user is the creative director. Confirmed intent overrides model or critic preference.
- Use this skill for taste discovery, direction comparison, or iterative rendered critique. Do not invoke it for a narrow fix with a specified outcome.
- Preserve product behavior unless the user approves a behavior change.

## Hard Rules

- Inspect the project, rendered baseline, tools, and `git status` first. Preserve all existing changes unless their owner authorizes replacement. Do not commit, reset, push, or switch branches without permission.
- Never issue a visual verdict or score without rendered evidence and vision. If either is unavailable, request captures or offer an explicitly unverified planning-only run.
- Before external transfer, identify the provider and exact project content, captures, recordings, or prompts involved; redact private data and obtain consent for that use. Never expose or store credentials. Use existing environment variables or request a narrowly scoped key. Keep sensitive captures temporary, delete them after review, and ask before retention.
- Confirm material costs before paid services.
- Use a fresh critic context where possible. Do not give it implementation rationale that could bias its verdict.
- Do not claim completion from a critic score alone. Completion also requires applicable verification, disclosed limitations, and user validation.

## Compact State

For every run, exclude `.taste-loop/` through `.git/info/exclude` and keep `state.md`; ask before changing tracked `.gitignore`. Replace stale state instead of appending a transcript. Retain only what is needed to resume:

```md
# Taste Loop State
project: <path>
branch: <branch>
base_revision: <revision>
last_observed_revision: <revision>
mode: <mode>
scope: <scope>
phase: <phase>
rounds_used: <used>/<budget>
approved_providers: <providers or none>

## Decisions
- D1 ACCEPTED: <direction or constraint>
- D2 REJECTED: <proposal and reason>

## Current Candidate
- score/tier: <value>
- evidence: <paths or URLs>
- accepted directives: <stable IDs>
- blockers: <items>
- verification: <checks, failures, and limits>
```

Before resuming, validate path, branch, revision history, and scope. If state conflicts, show why and ask whether to resume, archive, or replace it. Update state after decisions, phase changes, verdicts, or blockers, not routine commands.

## Modes

- **Quick Polish**: direction is known; one candidate and one correction round.
- **Guided**: compare up to three directions; use up to two correction rounds.
- **Full Studio**: prototype three to five researched directions; use up to three correction rounds.
- **Hands-off**: infer taste from available evidence, record assumptions, and use up to three correction rounds. Pause only for privacy, cost, blockers, or irreversible choices.

Ask only when the request does not imply a mode. The initial diagnostic verdict costs no round. Count a round after accepted corrections, corrected evidence, and a fresh verdict.

If the budget ends below acceptance, label it incomplete. Show evidence and blockers, then ask to extend, accept disclosed gaps, or stop.

## Run The Loop

1. **Inspect**: identify the stack, run path, routes, design system, responsive states, constraints, baseline revision, and rendered product.
2. **Choose scope and mode**: record what may change, what must not change, and the review budget.
3. **Resolve direction**: if taste is unclear or the mode is Guided, Full Studio, or Hands-off, read [`references/direction.md`](references/direction.md) before discovery or research. Get user approval unless Hands-off mode applies.
4. **Contract and build**: read [`references/build-and-evidence.md`](references/build-and-evidence.md) before editing. Define observable acceptance criteria, implement, run targeted checks, and capture comparable evidence.
5. **Critique and correct**: read [`references/critic-loop.md`](references/critic-loop.md) before the first verdict. Use independent criticism, adjudicate directives against user intent, and spend each round on the highest-impact accepted problems.
6. **Verify and exit**: at the threshold or a chosen exit, run the full applicable verification matrix. Record evidence and limits, then request final user validation.

Recommend acceptance when all are true:

- The design contract is satisfied.
- Applicable checks pass, or failures are clearly disclosed.
- An independent critic reaches `8/10`, unless criticism is unavailable and that limit is disclosed.
- No unresolved blocker conflicts with confirmed user priorities.

The user may knowingly accept a lower score or disclosed gap. Record that decision without presenting it as an unqualified pass.
