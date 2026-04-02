---
name: clarify-intent
description: Turn vague, underspecified, or ambiguous user requests into a compact execution artifact that clarifies the goal, boundaries, success conditions, missing context, and recommended persistence scope. Use when a request is fuzzy, several interpretations are possible, constraints are implicit, acceptance criteria are missing, or Codex needs to decide whether the clarified intent should remain temporary, become component-specific knowledge, or be stored project-wide.
---

# Clarify Intent

Convert an underspecified request into a compact artifact that another Codex instance can execute against with minimal ambiguity.

Prioritize speed and usefulness over exhaustiveness. Infer reasonable structure from the user's request, but make uncertainty visible instead of pretending it is resolved.

## Produce

Return a short artifact with these sections, in this order:

```markdown
Goal
- ...

Why it matters
- ...

Scope
- ...

Non-goals
- ...

Constraints
- ...

Acceptance criteria
- ...

Open questions
- ...

Context needed
- ...

Suggested storage scope
- temporary | component-specific | project-wide
- Reason: ...
```

Keep each section compact. Prefer short bullets over paragraphs.

For concrete patterns, see [references/examples.md](references/examples.md).

## Work Method

1. Extract the likely objective.
2. Separate what the user wants from what they did not ask for.
3. Make success testable.
4. Surface missing information as explicit open questions.
5. Decide how durable the clarified intent appears to be.

If the request is already precise, compress rather than expand. The goal is a sharper artifact, not a longer one.

## Inference Rules

- Write `Goal` as the concrete outcome the user is trying to achieve.
- Write `Why it matters` as the practical reason or expected value behind the request.
- Write `Scope` as the work that should happen now.
- Write `Non-goals` to block common overreach, adjacent work, and attractive but out-of-scope additions.
- Write `Constraints` from explicit requirements first, then cautious inferences that are likely true.
- Write `Acceptance criteria` as observable conditions that would let the user say the task is done.
- Write `Open questions` only for uncertainties that materially affect implementation or correctness.
- Write `Context needed` as the minimum missing information, files, decisions, or prior knowledge required to proceed well.

Do not fabricate precision. If a field is genuinely unknown, say so briefly and move the uncertainty into `Open questions` or `Context needed`.

## Storage Scope Decision

Choose exactly one:

- `temporary`: Use when the clarified intent only helps with the current conversation, a one-off fix, or a transient task setup.
- `component-specific`: Use when the intent expresses rules, expectations, or patterns that should be remembered for one feature, service, module, or bounded subsystem.
- `project-wide`: Use when the intent reflects stable standards, cross-cutting constraints, product principles, or durable workflow rules that should shape future work across the project.

Prefer the narrowest scope that preserves the value of the clarification.

Use these heuristics:

- Choose `temporary` if the artifact is mostly about immediate execution details.
- Choose `component-specific` if the artifact would likely be reused in the same area of the codebase.
- Choose `project-wide` if forgetting it would cause repeated mistakes across multiple areas.

Always include a one-line reason for the chosen scope.

## Interaction Rules

- Do not interrogate the user with a long questionnaire by default.
- First produce the artifact from available evidence.
- Ask only the smallest set of follow-up questions needed to remove high-risk ambiguity.
- If there are several plausible interpretations, choose the most likely one and list the others in `Open questions`.
- If the user explicitly asks for help refining a request, make the artifact the main output.
- If the user asks to proceed after clarification, treat the artifact as the current working contract unless they revise it.

## Quality Bar

The artifact is good if:

- another engineer could start implementation from it,
- likely scope creep is blocked by `Non-goals`,
- success is checkable from `Acceptance criteria`,
- missing information is explicit rather than hidden,
- and the storage recommendation is narrow, justified, and useful for future context handling.
