# Taste Loop Launch Plan

## Goal

Ship the smaller Taste Loop orchestrator without losing the behavior of the original skill. The launch should prove that progressive disclosure lowers the default context cost while preserving direction discovery, implementation, evidence capture, independent criticism, correction rounds, and final verification.

## Current Candidate

- Baseline: `934f0ce`, tagged `pre-token-optimization-v0.1.0`.
- Working branch: `optimize-token-efficiency`.
- `SKILL.md` is the compact orchestrator.
- `references/` contains conditional guidance for direction discovery, build and evidence, and the critic loop.
- `EVALS.md` covers the original workflows and the behavioral boundaries added during optimization.
- The core skill changed from approximately 2,894 words to 784 words before this plan was added.

## Launch Gates

1. Review the pull request against `pre-token-optimization-v0.1.0` for behavior loss, weak reference triggers, duplicated rules, and stale instructions.
2. Run the Skills CLI validation and the behavioral evaluation audit. Record the exact commands and results in the pull request.
3. Install the branch into a clean skills-compatible client and confirm that `SKILL.md` resolves all three reference files.
4. Run representative Quick Polish, Guided, and Hands-off sessions. Confirm that the agent respects user authority, privacy, dirty-worktree safety, round budgets, critic score gates, and final user validation.
5. Merge only after the pull request review finds no launch blocker.

## Rollout

1. Merge the optimization pull request to `main` as the soft launch.
2. Install from `main` with `npx skills add AbdulsaboorS/taste-loop` in a clean environment.
3. Use the skill on real projects with different stacks and viewport requirements. Capture only behavior failures or missing branches, not project-sensitive evidence.
4. Fix launch blockers in small follow-up pull requests. Keep workflow detail in conditional references unless every run needs it.
5. Announce the optimized version after representative sessions complete without a behavior regression.

## Recovery

If the optimized skill causes material regressions, stop the rollout and compare the failing branch with `pre-token-optimization-v0.1.0`. Restore the missing behavior in the narrowest relevant file. Revert the optimization only when the orchestrator and reference pointers cannot be corrected safely.

## Next-Agent Handoff

Start from `optimize-token-efficiency`. Inspect `git status`, the diff from `pre-token-optimization-v0.1.0`, and the pull request before editing. Do not broaden this change into new product features or a version bump. The next work is review and launch validation against the gates above. Keep the pull request unmerged until the user explicitly approves merging.
