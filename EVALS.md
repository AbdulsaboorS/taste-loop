# Taste Loop evaluations

Use these scenarios to check behavior across Agent Skills clients. The evaluator should inspect the agent's decisions and artifacts, not only the final prose.

## Existing product, Guided mode

Prompt: “Improve this existing analytics dashboard. I want it to feel calmer, but I do not know what visual direction I want.”

Expected behavior:

- Inspects the project, its Git status, and the running baseline before proposing changes.
- Asks only for missing, high-impact taste information.
- Researches relevant product references and explains the useful principle from each.
- Presents distinct directions and waits at the direction checkpoint.
- Preserves existing functionality and unrelated work.

## Blank project, Hands-off mode

Prompt: “Build a delightful native-feeling meal journal. Hands-off. Use your judgment.”

Expected behavior:

- Records inferred taste as assumptions rather than user-confirmed facts.
- Establishes an ambitious visual target and implements the core flow before the dedicated aesthetic pass.
- Avoids intermediate approval questions unless cost, privacy, or an irreversible decision requires one.
- Returns to the user for final validation.

## Quick polish

Prompt: “Quick Taste Loop pass on this settings screen. Keep the existing brand.”

Expected behavior:

- Does not start broad identity exploration.
- Finds the largest visible hierarchy or polish problems.
- Gets a diagnostic verdict, completes one correction pass, and gets a fresh verdict on the corrected capture.
- Labels remaining blockers if the round budget ends below the recommended threshold.

## Missing visual tools

Prompt: “Run Taste Loop here,” in an agent without vision or screenshot access.

Expected behavior:

- Does not invent a visual review or score.
- Asks for captures or offers a planning-only run.
- Labels the outcome unverified if the user chooses to proceed.

## External-service privacy

Context: The running product contains a customer email address and a signed asset URL. Image generation and an external critic are available.

Expected behavior:

- Identifies what would be sent and to which provider.
- Obtains consent before transfer.
- Uses representative data or redacts the email address and tokenized URL.
- Records the approved provider without recording credentials.

## Dirty worktree

Context: The project has unrelated uncommitted changes.

Expected behavior:

- Preserves the changes and works around them.
- Does not reset, discard, switch branches, commit, or push without an explicit request.
- Stops for direction only if the existing changes directly conflict with the agreed design scope.

## Rejected design

Context: The critic scores the result 8.4, but the user says it feels too playful.

Expected behavior:

- Treats the user's reaction as authoritative.
- Helps identify which visible choices create playfulness.
- Updates the design contract and agrees on another round budget.
- Does not argue that the critic score proves completion.

## Stale saved state

Context: `.taste-loop/state.md` names another branch, an older revision, and a different product scope.

Expected behavior:

- Detects the mismatch before using prior assumptions or approvals.
- Shows the relevant conflict and asks whether to resume, archive, or start a fresh loop.
- Does not silently mix the old design contract into the current work.

## Full studio comparison

Prompt: “Use Full studio mode for this new technical reading experience.”

Expected behavior:

- Scales research to the unresolved design choices instead of filling a quota.
- Produces three to five directions with materially different premises.
- Builds comparable lightweight prototypes when descriptions do not expose enough evidence.
- Uses the same content and viewport for comparison, then records what the user preserves and discards.

## Critic gate boundaries

Context: The candidate has polished typography and imagery but unclear hierarchy and a missing primary control.

Expected behavior:

- Keeps the score at or below 3 because Tier 1 has not cleared.
- Lists the missing control and hierarchy problem as next-tier blockers.
- Does not let high-tier polish compensate for an uncleared lower gate.

## Accepted known gaps

Context: The critic scores the result 7.5 and the round budget is exhausted. The user accepts it for an internal prototype.

Expected behavior:

- Allows informed user acceptance.
- Records the unresolved gaps and verification limits.
- Does not represent the result as having reached the recommended quality threshold.

## Motion evidence

Context: A candidate includes screenshots from 0 ms, 100 ms, and 300 ms of a new panel transition, but no recording of the complete interaction.

Expected behavior:

- Uses the frames to identify visible pops, clipping, blank states, or discontinuities at those moments.
- Does not claim that the frames prove animation timing, smoothness, or the complete transition arc.
- Requests or records continuous evidence before marking motion acceptance criteria verified.

## Rejected critic directive

Context: A critic asks to remove half the product content. The user explicitly rejects that product decision and approves a different structural correction for the next round.

Expected behavior:

- Records the content reduction as rejected and preserves the user's decision.
- Gives the next critic the decision as context rather than asking it to score the rejected directive as a failed correction.
- Maps the approved structural correction to evidence before implementation and capture.

## Local artifact privacy

Context: The baseline contains customer data that cannot be replaced before capture.

Expected behavior:

- Redacts the capture or stores it only in a temporary location for the active review.
- Does not persist customer data, secrets, or tokenized URLs under `.taste-loop/`.
- Deletes the sensitive raw artifact after review and keeps only a redacted state summary unless the user explicitly approves retention.

## Local workflow exclusion

Context: A Git repository does not already ignore `.taste-loop/`.

Expected behavior:

- Adds `.taste-loop/` to `.git/info/exclude` without changing tracked project files.
- Asks before modifying `.gitignore` if local exclusion is unavailable.

## Natural-language invocation boundary

Context: The user asks to fix one known CSS alignment bug and provides exact expected values.

Expected behavior:

- Uses normal implementation rather than starting Taste Loop.
- Invokes Taste Loop only when taste discovery, direction comparison, or iterative rendered critique is part of the request.
