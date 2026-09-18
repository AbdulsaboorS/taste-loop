# Critic Loop

## Independent Verdict

Give a fresh critic the contract, selected references, and rendered evidence, without implementation rationale. Later rounds also receive the previous candidate, verdict, and accepted directive IDs.

Use this compact prompt:

```text
Act as an independent design director. Judge only the supplied rendered product against its design contract and confirmed user priorities. Do not reward effort or infer hidden quality from source code.

Return:
- score /10 and highest cleared tier;
- tier blockers;
- the strongest successful decision;
- up to five prioritized directives with stable IDs and observable completion tests;
- for prior accepted IDs: LANDED, PARTIAL, or NOT LANDED, with evidence;
- uncertainty caused by missing evidence.
```

Apply gated score caps:

- **Tier 1, intent and hierarchy**: required content, controls, task, reading order, and emphasis. Cap at `3` until clear.
- **Tier 2, composition and language**: layout, type, palette, imagery, density, and platform fit. Cap at `5` until clear.
- **Tier 3, system and distinctness**: components, states, and direction hold beyond one hero area. Cap at `7` until clear.
- **Tier 4, polish and restraint**: spacing, alignment, assets, controls, and responsive compositions. Cap at `9` until clear.
- **Tier 5, reference quality**: original, appropriate work that holds beside selected professional references. Scores above `9` require this tier.

A lower-tier blocker enforces its cap.

## Adjudicate Directives

Classify each directive against the contract, user intent, usability, accessibility, and technical constraints:

- **ACCEPTED**: correct and in scope; assign a stable ID.
- **REJECTED**: conflicts with intent or evidence; record the reason so it does not return as a failure.
- **DEFERRED**: useful but outside current scope; record the boundary.

In Guided and Full Studio modes, show the verdict and recommendation; ask the user before a material correction. The critic advises. The user decides intent.

## Spend Rounds By Impact

Choose correction scale by score:

- Below `5`: fix structure, task flow, hierarchy, and missing states before style.
- From `5` to below `8`: strengthen the design system, composition, responsiveness, and consistency.
- At `8` or above: make only evidence-backed polish that protects the contract.

For each counted round:

1. Implement the highest-impact accepted directives.
2. Run targeted checks for changed behavior.
3. Capture comparable corrected evidence.
4. Obtain a fresh delta-aware verdict.
5. Update directive statuses, score, blockers, and state.

If a directive does not land, reassess the structure or ask about the tradeoff instead of repeating a local tweak. After two flat rounds or three repeats of one blocker, make one structural correction. Reduce scope only with user approval. Revert only a specific visible regression.

Stop when the core acceptance rules are met, the user makes an informed exit decision, or the round budget is exhausted. Budget exhaustion alone is never completion.

If the user rejects the final candidate, convert their reaction into directives and agree on a new round budget before continuing.
