# Examples

## Example 1

Input:

```text
Make the dashboard better for onboarding.
```

Output:

```markdown
Goal
- Improve the dashboard so new users understand what to do first and can reach an initial success state faster.

Why it matters
- Weak onboarding reduces activation and makes the dashboard feel confusing or empty.

Scope
- Clarify the first-run experience on the dashboard.
- Emphasize primary next actions for new users.

Non-goals
- Redesign the entire product.
- Rewrite unrelated account settings or billing flows.

Constraints
- Preserve the existing dashboard as the main entry point.
- Avoid changes that require a full information-architecture rewrite.

Acceptance criteria
- A new user can identify the next recommended action within a few seconds.
- The dashboard shows a clear first-run path instead of a generic empty state.

Open questions
- Which user segment is "new users" referring to?
- Is the issue copy, layout, missing product guidance, or all three?

Context needed
- Current dashboard screenshots or code.
- Existing onboarding metrics or known pain points.

Suggested storage scope
- component-specific
- Reason: this clarification appears to define expectations for one product surface, not the whole project.
```

## Example 2

Input:

```text
Set up the repo so changes always get tested before merge.
```

Output:

```markdown
Goal
- Establish a pre-merge testing rule so code changes are validated automatically before they are merged.

Why it matters
- This reduces regressions and makes repository quality checks consistent.

Scope
- Define and enforce the required automated checks for pull requests.

Non-goals
- Redesign the full deployment pipeline.
- Replace the team's existing test framework.

Constraints
- Work with the current repository and CI setup if possible.
- Keep feedback fast enough for normal development use.

Acceptance criteria
- Pull requests cannot merge without the required checks passing.
- The required checks are clearly defined and run automatically.

Open questions
- Which test suites are mandatory versus optional?
- Which merge system is in use?

Context needed
- Current CI configuration.
- Branch protection settings.
- Test command inventory.

Suggested storage scope
- project-wide
- Reason: this is a durable workflow rule that should affect the whole repository.
```
