---
name: ub-mode
description: >-
  Use when the user invokes $ub-mode (or /ub-mode), asks for the engineering workflow
  published by Uncle Bob, or specifically requests test-first changes,
  root-cause repair, rigorous refactoring and a change-by-change audit log.
  Apply the three-stage ub-mode sequence to code-writing and code-editing work.
---

# ub-mode: disciplined software changes

**Origin and credit:** This skill is an *independent adaptation* inspired by
the `ub-mode` workflow published by **Robert C. Martin (Uncle Bob)**:
https://github.com/unclebob/ub-mode/blob/master/SKILL.md

It is **not the original SKILL.md**, is not an official port, and is not
affiliated with or endorsed by the original author. Read
[attribution and provenance](references/ATTRIBUTION.md) when provenance or
redistribution is relevant. The original project's README also acknowledges
influence from @poteto's `poteto-mode` / `pstack` rules.

## Invocation and boundaries

Apply when the user invokes `$ub-mode`, selects this skill, or explicitly asks
for this workflow. For an implementation task, proceed through these three
stages, in order:

1. **First Make it Work:** establish the desired behavior with minimal,
   verifiable changes.
2. **Then Make it Right:** repair root causes, simplify the design and validate
   quality.
3. **Practice:** maintain evidence, change records and safe repository hygiene.

Do not create code or run destructive commands in a review-only request. Use
the project's languages, style, testing framework and documented conventions.
User instructions, repository policies and safety constraints take precedence
over this workflow.

## Stage 1: First Make it Work

### Define a checkable destination
- Briefly state the specific user-visible outcome and an objective way to
  verify it.
- Inspect the relevant data model, tests and boundaries before editing.
- Prefer the simplest change that addresses the requirement.
- Make the affected decisions in one authoritative location; avoid mirrored
  configuration and repeated special cases.
- When the current design would be awkward for a new requirement, sketch the
  design that would have existed had the requirement been present initially.
  Migrate toward it in safely verifiable increments instead of stacking
  exceptions on top of exceptions.
- Favor removing unnecessary paths, branches and layers before adding more.

### Red, green, minimal
- For behavior that can be honestly tested, add a test of the expected outcome
  before implementation and run it to observe the expected failure.
- Implement only enough to make that test pass; rerun the focused test.
- Prefer assertions against public behavior, not private methods or incidental
  implementation details.
- If a legitimate automated test is infeasible, state why and choose a
  meaningful alternative such as a reproducible CLI invocation, fixture,
  integration check or manual acceptance procedure. Do not invent a test for
  appearance's sake.

### Data and concurrency
- Design values and domain types so impossible combinations are rejected or
  cannot be represented.
- Validate and normalize untrusted input once at the entry boundary.
  Internal business rules should receive parsed values, not reparse the
  outside world on every call.
- Keep domain decisions in deterministic, side-effect-light functions where
  feasible. Do not silence compiler/type errors merely to proceed.
- Minimize mutable shared state. Separate owners that do not need to share;
  when sharing is required, enforce a single writer or an equivalent safe
  coordination design.
- Prefer idempotent operations, including safe retries after a crash or an
  interrupted run.
- Maintain the local domain vocabulary. Avoid speculative abstractions when
  the existing implementation is already clear.

### Re-examine a failing hypothesis
- When two attempts based on the same assumption fail the same verification
  gate, stop changing symptoms. Write the assumption explicitly, identify
  which components depend on it, and redesign the allocation of responsibility
  before trying another patch.

### Automate repeated work
- When repetition is substantial or error-prone, solve one representative
  instance manually, then construct a script or tool that reproduces it.
  Avoid building automation when the direct edit is simpler.

## Stage 2: Then Make it Right

### Fix the cause and work in slices
- Reproduce bugs and trace failures to their owning cause. A condition that
  merely suppresses an exception without removing the defect is not
  sufficient.
- Complete one small change, verify it, and only then advance.
- Before refactoring, capture current externally observable behavior.
  Restructure internal code while showing the behavior remains stable.
- Remove unused code only after proving nothing still depends on it.

### Quality gates
Consult [quality gates](references/QUALITY_GATES.md) for the official
companion-tool repositories and honest fallbacks.

1. **Crapper:** Where available and compatible, inspect function-level CRAP
   scores. The original ub-mode target is **strictly below 10**. Reduce risk
   through clearer composition, added relevant tests, or both.
2. **Dryer:** Where available and compatible, inspect reported duplication.
   Treat similarity **at or above 0.8** as a candidate for eliminating
   redundant logic, while preserving meaningful domain distinctions.
3. **Mutator:** Where available and compatible, inspect uncovered behavior
   and surviving mutations. Improve the meaningful tests and remove dead code
   where justified.
4. Rerun the project's normal test suite, formatting, static analysis and
   build verification as appropriate.

These tools are **not bundled or installed** with this plugin. Never claim a
gate passed unless the tool actually ran and its output was inspected. If a
tool cannot be used, mark that gate **not run** and explain the reason; do not
substitute guessed scores or claim equivalent measurement.

## Stage 3: Practice

### Preserve an auditable action log
- Maintain a concise record of the action, why it was necessary and what
  evidence supports the result (test, build, diff or inspected command output).
- Summarize the log in the final response, including changed paths, meaningful
  decisions, verification results and unresolved risks.
- Prefer compact summaries and referenced artifacts over flooding the main
  thread with transcripts.

### Leave the repository safe
- Inspect status and diff before cleanup. Never delete untracked or uncommitted
  user work merely because it seems unused.
- Clean temporary worktrees and generated artifacts only if they are verified
  safe to remove.
- Make small, coherent commits **only when the user has authorized commits**.
  A commit message should explain purpose, meaningful change and verification.
- Push **only when authorized** and to the user-approved remote and branch.
  Do not assume permission to push to `main`, force-push, rewrite history or
  bypass branch protections. The upstream workflow calls for regular commits
  and a final push; this adaptation deliberately respects explicit permission
  and repository governance.

## Required completion report

Report:
- **Outcome:** what behavior was delivered or why completion is blocked.
- **Change log:** concise sequence of actions and reasons, with affected files.
- **Verification:** actual commands/checks and pass/fail/not-run status.
- **Quality gates:** Crapper, Dryer and Mutator, each with measured evidence or
  a clear `not run`; list thresholds only when applicable.
- **Repository state:** commits/pushes performed (if any), or explicitly none.
- **Remaining issues:** unresolved risks, skipped checks and next steps.

Do not overstate certainty, tool availability, testing or author endorsement.
