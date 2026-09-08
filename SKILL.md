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

Turn the user's taste into an explicit design direction, build it, inspect the real result, and loop until the user accepts the quality.

The user is the creative director. Help them form and express taste; do not replace it with average model preferences. Judge the rendered product, not the effort or code behind it.

## Start

1. Inspect the project before proposing a direction. Identify its platform, audience, purpose, current visual language, design system, technical limits, and how to run it.
2. Check the available capabilities: web research, image input and generation, video generation, subagents, browser or simulator control, screenshot capture, screen recording, and frame extraction. A verified visual loop requires rendered evidence and vision. If either is unavailable, ask the user to provide captures or offer a clearly labeled planning-only run; never issue a visual score without visual evidence.
3. Inspect repository status before editing. Preserve all existing changes and constrain edits to the agreed product scope. Do not commit, push, switch branches, reset, discard changes, or rewrite unrelated work unless the user explicitly requests it.
4. Resume from `.taste-loop/state.md` only after checking that it still matches the current project. Ask before using stale or conflicting state. Otherwise create `.taste-loop/`. In a Git repository, exclude it through `.git/info/exclude`; ask before changing the project's `.gitignore` if a local exclude is unavailable. Keep final product code in its normal project locations.
5. Keep a minimum state header with project path, branch and revision, mode, product scope, current phase, completed and allowed round counts, approved external providers, and unresolved decisions. Update it at every checkpoint so a later run can validate and resume safely.
6. Select a mode from the user's request. If the intended mode is unclear and the choice would materially change the work, ask once:
   - **Quick polish:** Preserve the direction, fix the largest visual problems, and run one review round.
   - **Guided:** Explore up to three useful directions with decision checkpoints, then run up to two review rounds. This is the default.
   - **Full studio:** Research broadly, explore three to five useful directions, prototype promising options, and run up to three review rounds.
   - **Hands-off:** Infer taste from the request and project, choose the direction, and run up to three review rounds without approval pauses. Ask only for required privacy consent, a hard blocker, or an irreversible, costly choice.
7. State the selected mode, planned review-round limit, and any capability gaps. A review round starts from an initial candidate verdict, applies one prioritized correction pass, and ends with a corrected capture and fresh critic verdict. The diagnostic verdict before the first correction does not consume a round. Warn before work that can incur material API cost. Never expose or persist credentials; use existing environment variables or ask the user to configure a narrowly scoped key.
8. Before capturing or recording, replace private content with representative data or redact it. Never persist secrets, private customer content, or tokenized URLs in `.taste-loop/` or another artifact directory. Before sending project content, screenshots, recordings, or prompts to an external model or service, identify the provider and data involved and obtain consent unless the user has already authorized that exact use. Record approved external providers in `.taste-loop/state.md`.

The round limit is a default budget, not a quality claim. When it is exhausted before validation, show the current evidence and remaining blockers, label the result incomplete, and ask whether to extend, accept the known gaps, or stop.

## Discover

### Establish the baseline

Run the product and capture its important screens, states, and viewport sizes. For a new product, inspect its requirements and closest functional peers instead. Add the baseline, constraints, assumptions, and approvals to `.taste-loop/state.md` under its minimum state header.

Preserve established product conventions unless the user wants a new identity. Do not turn a focused refinement into an unsolicited redesign.

### Elicit taste

Ask about decisions the user can react to, not design jargon they must invent. Adapt the questions to what is already known. Cover only the missing high-impact areas:

- The audience, task, and feeling the product should create.
- What should attract attention first and what should stay quiet.
- Products, interfaces, physical spaces, media, or eras they like.
- Specific elements they like and dislike in those references.
- Preferred density, typography character, color behavior, imagery, and motion.
- What would make the result feel generic, inappropriate, or unlike them.
- Accessibility, brand, platform, performance, and asset constraints.

When feedback is vague, offer concrete interpretations instead of demanding vocabulary. For example: “When you say it feels cheap, is the main cause the glossy effects, crowded spacing, playful type, or something else?” Record confirmed preferences as evidence, not permanent laws.

In hands-off mode, infer these answers from the product and request. Mark them as assumptions in `.taste-loop/state.md`.

### Research inspiration

Research sources that fit the product rather than browsing every gallery:

- Product flows and mobile patterns: Mobbin, Refero, Page Flows, Screenlane.
- Marketing and expressive web work: Awwwards, SiteInspire, Land-book, Godly, One Page Love.
- Broad visual exploration: Dribbble, Behance, Are.na, design-studio portfolios.
- Platform conventions: Apple Human Interface Guidelines, Material Design, Microsoft Fluent, and the target platform's primary guidance.
- Domain products: direct and adjacent competitors, including products outside the user's industry that solve a similar interaction problem.

Collect only enough references to expose meaningful choices and establish a quality bar. Scale the research to uncertainty, scope, and budget; stop when new references repeat known ideas. Prefer primary pages and working products over gallery thumbnails. For each reference, record its URL, what is relevant, what is not, and the principle it suggests. Never claim to have inspected an inaccessible page. Ask the user for screenshots or links when authentication or tooling blocks research.

Treat references as a moodboard and quality baseline. Extract composition, hierarchy, type, color, texture, interaction, and restraint principles. Do not copy a complete design, signature illustration, brand identity, or proprietary asset.

### Expand the possibility space

Create genuinely distinct directions rather than small style variations. Each direction must state:

- Its central idea and intended emotional response.
- Composition and information hierarchy.
- Typography, color, texture, imagery, and motion.
- How it serves the product and audience.
- Its biggest risk or likely failure mode.

Use one or both of these techniques when they add value:

**Ambitious direction:** Connect the product to a specific, unusual visual world or interaction premise. Be concrete enough to constrain decisions while leaving room for execution. “An editorial field guide whose data behaves like specimens” is useful; “unique and beautiful” is not.

**Seed variation:** When the space is blank or the directions are converging, generate external entropy with an available secure random command. Interpret patterns in the value as prompts for layout, rhythm, palette, type, or motion. The seed is creative pressure, not visible product content and not a substitute for judgment.

Avoid averaging directions together. A direction should have a point of view.

### Direction checkpoint

In Guided and Full studio modes, present the directions visually when tools permit. Ask the user to select, reject, or combine principles. Draw out useful reactions:

- Which direction feels most appropriate rather than merely impressive?
- What should be preserved at all costs?
- What is the first thing they would remove?
- Which reference best represents the desired quality bar?
- What feels too familiar, decorative, loud, sterile, or impractical?

Translate the response into explicit design decisions and anti-goals. Ask in small batches and stop when the high-impact uncertainty is resolved. In Full studio mode, build lightweight, disposable prototypes of the promising directions when static descriptions cannot resolve the choice. Compare them using the same content and viewport, then ask what to preserve and discard. Confirm the direction before production implementation. The checkpoint is complete only when one coherent direction and its quality references are selected.

If image generation is available and a rendered concept would clarify the direction, generate a target image or small moodboard. Iterate on obvious generation failures before showing it. Treat it as an ambition target, not a pixel specification. Product usability and real content take priority over matching generated art.

## Define

### Write the design contract

Record the approved direction in `.taste-loop/intent.md`:

- Product, audience, and primary task.
- Intended feeling and central visual idea.
- Chosen references and the principle taken from each.
- Hierarchy, composition, typography, color, texture, imagery, and motion.
- Important screens, responsive states, interactions, and transitions.
- Constraints, anti-goals, and elements that must remain.
- Observable acceptance criteria.

Write intent and reasons, not only implementation outcomes. This file is the source of truth after context compression or handoff.

### Build a focused first pass

Separate functional architecture from aesthetic attention when practical. If functionality does not exist, establish the core flow first, then make a dedicated visual pass. If it already exists, preserve behavior while changing presentation.

Implement the selected direction across the full visible system, not only the hero frame. Make the first pass coherent enough to review:

- Use real or representative content rather than idealized placeholders.
- Cover loading, empty, error, selected, focused, and disabled states that matter.
- Preserve native behavior where custom behavior adds no meaningful value.
- Give important details enough attention to support the central idea.
- Keep code maintainable and consistent with the project.

Use generated images when they add product-specific meaning or a visual layer code alone cannot provide. Establish a consistent art direction before generating a set. Optimize assets and include appropriate text alternatives or decorative treatment.

Use generated video only when motion is central and coded animation cannot reasonably produce the effect. Design a reduced-motion or static fallback, control loading cost, and verify continuity at loop or state boundaries. Do not add image or video generation merely to demonstrate the tool.

### Capture the candidate

Run the real product. Capture the candidate at the same important states and viewport sizes as the baseline. Include reference images or the approved target at comparable dimensions where possible. Self-review before invoking a critic; fix obvious breakage first.

Before capture, map each intended improvement to evidence that can prove or disprove it. Include the complete composition and any close view needed to judge detail. Do not spend a review round on a change whose claimed benefit is absent from the evidence.

For motion, record the complete interaction from before the trigger through the settled state. Inspect the start, end, and meaningful intermediate frames. Use frame extraction or pixel-difference tools when available to locate pops, unintended jumps, blank frames, clipping, flicker, or discontinuity. Selected static frames can diagnose defects but cannot prove timing, smoothness, or the full transition arc. Do not describe motion as verified when only static frames were checked.

### Invoke a fresh critic

Use a fresh, strong vision-capable subagent when available. Keep implementation details, code, effort, and internal rationale out of its context. On the first round, provide only the candidate captures, approved direction, relevant quality references, and the rubric. On later rounds, also provide the previous candidate and verdict so the critic can check whether directives landed.

If subagents are unavailable, use a fresh external agent or context. As a last resort, perform the review directly and tell the user that independence is reduced.

Give the critic this task:

> Act as an independent design director. Review the rendered product against its approved direction and quality references. Judge visible results, not implementation effort. Apply the gated rubric strictly; a candidate cannot score above a tier until it clears the lower tiers.
>
> - **Tier 1, intent and hierarchy:** Required content and controls are present. The primary task, reading order, grouping, and emphasis are clear. Cap the score at 3 until this fully clears.
> - **Tier 2, composition and language:** Layout, typography, palette, imagery, density, and platform fit form a coherent expression of the approved direction. Cap the score at 5 until this fully clears.
> - **Tier 3, system and distinctness:** Components and states feel related, the idea extends beyond one hero area, and the result avoids unearned conventions or decoration. Cap the score at 7 until this fully clears.
> - **Tier 4, polish and restraint:** Spacing, alignment, type details, assets, controls, and responsive compositions hold up under close inspection. Every prominent element earns its place. Cap the score at 9 until this fully clears.
> - **Tier 5, reference quality:** The work holds up beside the selected professional references while remaining original and appropriate to this product. A score above 9 requires this tier to clear.
>
> Put the score and highest cleared tier first. Then list blockers for the next tier. Give at most four additional directives, ordered by likely quality gain. Every directive must name the element, explain the visible problem, and prescribe a concrete change. If a previous verdict exists, mark each prior directive LANDED, PARTIAL, or NOT LANDED before adding new feedback. Flag uncertainty when a capture does not provide enough evidence.

The critic advises; it does not control product intent. Reject feedback that conflicts with confirmed user taste, usability, accessibility, or technical constraints, and record why.

### Review checkpoint

In Guided and Full studio modes, show the candidate and summarize:

- What changed and which intended qualities landed.
- The critic's score, blockers, and strongest directives.
- Your recommendation about which feedback to apply or reject.
- Focused questions tied to visible choices.

Ask for reactions before starting another material direction change. Translate reactions into updates to `.taste-loop/intent.md`. Record each critic directive as accepted, rejected, or deferred, with the reason. On the next round, ask the critic to judge only accepted prior directives; rejected product decisions are context, not failed corrections. The checkpoint is complete when the next round has a short, prioritized change set and evidence planned for each change.

## Deliver

### Iterate by impact

Address the next-tier blockers and the few changes with the largest visible gain. Do not spend a round polishing tiny details while composition or hierarchy remains wrong. Recapture the same evidence and invoke a fresh critic with the same rubric.

If the score fails to improve materially for two rounds, or the same blocker appears three times, stop tuning parameters. Identify the approach that is capping quality and make one structural change: revise the composition, asset strategy, type system, interaction model, or visual premise. If a structural attempt also stalls, explain the constraint and offer options rather than burning more rounds.

Treat small score changes as critic noise. Revert only the specific change that visibly regressed the work; do not discard unrelated improvements.

### Subtraction pass

After the direction works, remove anything that does not improve comprehension, hierarchy, interaction, or the intended feeling. Audit:

- Repeated explanations and labels that visible content already communicates.
- Containers, cards, badges, dividers, and controls without a functional role.
- Effects, gradients, glows, colors, and motion without a directional purpose.
- Custom components that communicate less clearly than a suitable native control.
- Empty space that weakens rather than focuses composition.
- Visual variety that breaks the system instead of adding useful emphasis.

Rebalance after removal. Subtraction is complete when every prominent element has a reason tied to the design contract.

### Verify the product

Verification must exercise the rendered product, not only run code checks. Cover what applies:

- Primary flows and interactive states.
- Narrow mobile, wide desktop, and relevant intermediate sizes.
- Short, long, missing, and realistic content.
- Keyboard navigation, focus visibility, semantics, contrast, text scaling, and reduced motion.
- Loading behavior, asset failures, and runtime errors.
- Animation continuity and frame-level glitches.
- Performance targets and asset cost.
- Existing automated checks required by the project.

Document tools used, evidence captured, failures found, and unresolved limitations in `.taste-loop/state.md`.

### Exit

Recommend final acceptance when:

- The implementation satisfies the design contract and required functionality.
- Applicable verification checks pass, or remaining failures are clearly disclosed.
- The independent critic scores it at least 8/10, or visual criticism was unavailable and that limitation is explicit.
- No unresolved blocker contradicts the user's stated priorities.

Show the final product and ask the user whether it feels valid to them. The user may knowingly accept a result below the recommended threshold; record the accepted gaps. A score never overrides the user. If they reject it, help turn their reaction into a concrete change and continue within a newly agreed round budget. In hands-off mode, this final validation is the required user checkpoint.

When complete, summarize the direction, evidence, verification, remaining tradeoffs, and files changed. Keep `.taste-loop/intent.md` and the redacted state summary available for later refinements. Delete raw captures and recordings that contain private product data; if retaining them has value, ask the user first and record the retention decision.
