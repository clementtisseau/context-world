# context-world
The context operating system for human-LLM software development.

Its purpose is to make sure that:

- the user can clearly express what they want,
- the project's important knowledge is stored in the right place,
- the LLM knows how to find and interpret that knowledge,
- the LLM notices when context is missing,
- and the LLM actively helps grow and maintain that context over time.

## Direction

The project goal is to implement a set of Codex skills that improve how intent, context, and durable project knowledge are handled during software work.

These skills should not only help Codex complete tasks. They should also help decide:

- what the user is actually asking for,
- what information is still missing,
- what should be kept only for the current task,
- and what should be promoted into reusable project context.

## First skill

The first skill is `clarify-intent`.

Its role is to take vague or underspecified requests and turn them into a compact working artifact that can guide execution and suggest the right storage scope for the resulting context.
