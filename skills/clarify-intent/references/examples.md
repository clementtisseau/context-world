# Examples

## Example 1

Input:

```text
Make the dashboard better for onboarding.
```

Output:

```markdown
I need a bit more context before I can turn this into an execution-ready brief.

Questions
1. Is the main problem activation, feature discovery, or reducing confusion on first login?
2. Should this work target brand-new users only, or also returning users who have not finished setup?
3. Do you want a UX/content improvement brief only, or should implementation-ready UI changes be included?

Why these matter
- Each answer changes the likely scope, the success criteria, and whether this is primarily a product-writing task, a UX task, or a code change.
```

After user answers:

```markdown
Goal
- Improve the dashboard so new users understand what to do first and can reach an initial success state faster.

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

Additional context needed
- Current dashboard screenshots or code.
- Existing onboarding metrics or known pain points.
```

## Example 2

Input:

```text
Set up the repo so changes always get tested before merge.
```

Output:

```markdown
I need a bit more context before I can turn this into an execution-ready brief.

Questions
1. Which git hosting system is in use: GitHub, GitLab, or something else?
2. Should every pull request be blocked on the full test suite, or only on a required subset?
3. Do you want this enforced through CI, branch protection rules, or both?

Why these matter
- The enforcement mechanism, required checks, and implementation path depend directly on these choices.
```

After user answers:

```markdown
Goal
- Establish a pre-merge testing rule so code changes are validated automatically before they are merged.

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

Additional context needed
- Current CI configuration.
- Branch protection settings.
- Test command inventory.
```
