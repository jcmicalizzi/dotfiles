---
description: Creates a PR that squashes the commits into one, uses the PR template, and updates Jira.
---
Follow this exact workflow to create a PR:
1. Rebase the branch with main.
2. Squash all commits on the branch into one, keeping only the commit message from the first (oldest) commit.
3. Force-push the squashed branch. Push is blocked by the administrator so provide a push command to run in another terminal.
4. Analyze the squashed commit and review the full diff against the base branch.
5. If there are tests or documentation missing from, request that they are created/updated before continuing.
6. Fill in the PR template at `.github/pull_request_template.md` as the PR body, completing all sections based on the analysis. If no template exists, use a structured format with summary, changes made, testing, and checklist.
7. Create the PR using `gh pr create` with the filled-in template.
8. Move the associated Jira ticket, if it exists, to "In Review" status. Infer the ticket ID from the branch name (e.g., `DATENG-431-description` → `DATENG-431`).
