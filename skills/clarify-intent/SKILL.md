---
name: clarify-intent
description: Ask the user a small set of high-value questions to extract missing intent, constraints, and success conditions from an underspecified request. Then rewrite the request as a compact execution brief and use that brief as the working contract for the next implementation step. Use when the user's request is vague, incomplete, ambiguous, missing acceptance criteria, or likely to lead to poor implementation without clarification.
---

# Clarify Intent

Your job is to turn an underspecified user request into an execution-ready brief by first extracting the missing information from the user.

This skill is interactive by default.

Do not jump straight into implementation when important intent is missing.

## Goal

When invoked on a vague or incomplete request:

1. Ask the user a small number of targeted clarification questions.
2. Use the user's original request plus their answers to build a compact, readable execution brief.
3. Treat that brief as the current working contract for implementation.
4. Then proceed with execution if the user asked to continue, or stop after producing the brief if they only asked for clarification.

## Default Behavior

Assume that the purpose of this skill is to extract missing information from the user before implementation.

Do not start by producing a final brief unless the request is already sufficiently clear.

If important information is missing, ask questions first.

Stop asking questions once the task is implementable with acceptable risk.

## Clarification Threshold

Ask follow-up questions first if any of these are true:

- several plausible interpretations would lead to materially different implementations,
- the success conditions are unclear,
- key scope boundaries are missing,
- important constraints are implicit or unknown,
- project-specific intent is needed and cannot be safely inferred,
- proceeding now would likely create messy, misaligned, or over-scoped code.

If the request is already sufficiently clear, produce the execution brief directly.

## Questioning Rules

Ask a small batch of questions first.

Rules:

- Ask at most 5 questions in one batch.
- Ask only questions whose answers would materially affect implementation, correctness, scope, UX, architecture, or persistence.
- Prefer concrete and constrained questions over open-ended ones.
- Prefer "which of these?" or "should this apply to X or Y?" over broad prompts.
- Do not ask for information that can be recovered from the repository or existing context.
- Do not ask questions whose answers can be safely deferred until implementation.
- Do not overwhelm the user with a long questionnaire.
- If multiple clarifications are needed, ask the highest-value ones first.

When asking questions, return this format:

    I need a bit more context before I can turn this into an execution-ready brief.

    Questions
    1. ...
    2. ...
    3. ...

    Why these matter
    - ...

Do not produce the final brief yet in this mode.

## After the User Answers

Once the user answers the clarification questions:

- combine the user's original request with the new information,
- resolve as much ambiguity as possible,
- make any remaining uncertainty explicit,
- rewrite the request into the execution brief below,
- and treat that brief as the current working contract.

If the user asked to proceed, continue into implementation using that brief, rather than starting another broad clarification round, unless a blocking ambiguity still remains.

## Produce

Return a compact execution brief with these sections, in this order:

    Goal
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

    Additional context needed
    - ...

Keep each section compact.

Prefer short bullets over paragraphs.

## Field Rules

- `Goal`: the concrete outcome the user wants.
- `Scope`: what should be done now.
- `Non-goals`: what should explicitly not be done now.
- `Constraints`: requirements, limitations, compatibility expectations, architectural boundaries, or user-imposed conditions.
- `Acceptance criteria`: observable conditions that make the task done.
- `Open questions`: only unresolved issues that still materially affect implementation.
- `Additional context needed`: the minimum additional repository, product, or architectural context still needed to execute well.

## Execution Handoff Rule

If the user asked for clarification only, stop after producing the execution brief.

If the user asked to proceed, use the execution brief as the working contract for the next implementation step.

Do not ignore the clarified brief during implementation.

## Interaction Rules

- Be proactive in identifying what is missing.
- Be economical in the number of questions.
- Make uncertainty visible instead of pretending it is resolved.
- Do not fabricate precision.
- Do not over-expand a request that is already clear.
- Do not ask broad questions just to be safe.
- Clarify first, then rewrite cleanly, then execute.

## Quality Bar

The result is good if:

- the user was asked only the minimum useful questions,
- the final brief reflects both the original request and the extracted information,
- another Codex run could execute from the brief with low ambiguity,
- scope creep is blocked by `Non-goals`,
- success is checkable from `Acceptance criteria`,
- and unresolved uncertainty is explicit.
